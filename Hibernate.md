## Hibernate

### 1.什么是Hibernate?

* Hibernate是一个持久层的ORM框架
* ORM: Object Relational Mapping 对象关系映射。将Java中的对象与数据库的表建立一种映射关系。

### 2.步骤

####one:创建数据库表

#### two:创建实体类

#### three:创建映射文件xxx.hbm.xml

* hibernate-mapping

* class：建立类与表的映射关系

  * name

    > 类的全路径名

  * table

    > 数据库表名

* id：建立类中属性与表中主键对应关系

  * generator：标签（主键生成策略）

    * native
    * uuid
    * identity
    * sequence
    * increment
    * assigned

  * name

    > 类中属性名

  * column

    > 表中字段名

  * length

    > 长度

  * type

    > 类型

* property：普通属性

  * name
  * column
  * length
  * type
  * not-null
  * unique

* set

  * key

    > 多的一方外键名称

  * many-to-many

  * many-to-one

  * one-to-many

  * one-to-one

#### four:创建Hibernate核心配置文件hibernate.cfg.xml

* 必须配置
  * 连接数据库参数
    * 驱动类
    * url路径
    * 用户名
    * 密码
  * 方言
* 可选配置
  * 显示SQL
  * 格式化SQL
  * 自动创建数据库表
    * create
    * update
    * validate
    * create-drop
    * none
* 引入映射文件
  * <mapping  resource=""  />

### 3.Hibernate核心api

* Configuration：加载配置文件

  * 加载核心配置文件

    * hibernate.properties

      >  Configuration configuration = new Configuration();

    * hibernate.cfg.xml  *********

      >  Configuration configuration = new Configuration().configure();

* SessionFactory：session工厂

  * 配置c3p0连接池hibernate.cfg.xml

  * 创建sessionFactory：buildSessionFactory()

  * 创建sesssion：openSession()

    * session 中的api

      * save

      * get

      * load

      * update

      * delete

      * saveOrUpdate

      * createQuery：HQL

        * 查询所有

          ```java
          //1  使用简单类名 ， 存在自动导包
          		// * Customer.hbm.xml <hibernate-mapping auto-import="true">
          		Query query = session.createQuery("from Customer");
          //2 使用全限定类名
          		Query query = session.createQuery("from com.itheima.a_init.Customer");
          		
          		List<Customer> allCustomer = query.list();
          
          ```

        * 选择查询

          ```java
          		//1 指定数据，cid OID名称
          		Query query = session.createQuery("from Customer where cid = 1");
          		//2 如果使用id，也可以（了解）
          		Query query = session.createQuery("from Customer where id = 1");
          		//3 对象别名 ,格式： 类 [as] 别名
          		Query query = session.createQuery("from Customer as c where c.cid = 1");
          		//4 HQL不允许使用*，查询所有项，mysql--> select * from...
          		Query query = session.createQuery("select c from Customer as c where c.cid = 1");
          
          		//uniqueResult()用于返回唯一结果
          		Customer customer = (Customer) query.uniqueResult();
          
          ```

          

        * 投影查询

          ```java
          //默认
          Query query = session.createQuery("select c.cid,c.cname from Customer c");
          
          //提供相应构造方法
          Query query = session.createQuery("select new Customer(c.cid,c.cname) from Customer c");
          
          List<Customer> allCustomer = query.list();
          ```

          

        * 排序

          ```java
          Query query = session.createQuery("from Customer order by cid desc");
          		
          List<Customer> allCustomer = query.list();
          
          ```

          

        * 分页

          ```java
          		Query query = session.createQuery("from Customer");
          		// * 开始索引 , 算法： startIndex = (pageNum - 1) * pageSize;
          		// *** pageNum 当前页
          		query.setFirstResult(0);
          		// * 每页显示个数 ， pageSize
          		query.setMaxResults(2);
          		
          		List<Customer> allCustomer = query.list();
          
          ```

          

        * 绑定参数

          ```java
          		//方式1：占位符?
          		Query query = session.createQuery("from Customer where cid = ?");
          		//0：表示参数的位置，是第几个，从0开始
          		//cid：实际参数
          		//setInteger()
          		//setString()
          		query.setInteger(0, cid);
          
          		//方式2：别名
          		Query query = session.createQuery("from Customer where cid = :xxx");
          		//query.setInteger("xxx", cid);
          		query.setParameter("xxx", cid);
          		
          		Customer customer = (Customer) query.uniqueResult();
          
          ```

          

        * 聚合函数和分组

          ```java
          		//1 
          		Query query = session.createQuery("select count(*) from Customer");
          		//2 别名
          		Query query = session.createQuery("select count(c) from Customer c");
          		//3 oid
          		Query query = session.createQuery("select count(cid) from Customer");
          		
          		Long numLong = (Long) query.uniqueResult();
          
          ```

          

        * 连接查询

          ```java
          //左外连接
          List list = session.createQuery("from Customer c left outer join c.orderSet ").list();
          //迫切左外链接 (默认数据重复)
          List list = session.createQuery("from Customer c left outer join fetch c.orderSet ").list();
          //迫切左外链接 (去重复)
          List list = session.createQuery("select distinct c from Customer c left outer join fetch c.orderSet ").list();
          
          ```

          

        * 命名查询

      * createSQLQuery

      * createCriateria：QBC

        * 简单查询

          ```java
          List<Customer> list = session.createCriteria(Customer.class).list();
          ```

          

        * 分页查询

          ```java
          		Criteria criteria = session.createCriteria(Order.class);
          		criteria.setFirstResult(10);
          		criteria.setMaxResults(10);
          		List<Order> list = criteria.list();
          
          ```

          

        * 排序查询

          ```java
          		Criteria criteria = session.createCriteria(Customer.class);
          		//criteria.addOrder(org.hibernate.criterion.Order.asc("age"));
          		criteria.addOrder(org.hibernate.criterion.Order.desc("age"));
          		List<Customer> list = criteria.list();
          
          ```

          

        * 条件查询

          ```java
          		// 按名称查询:
          		/*Criteria criteria = session.createCriteria(Customer.class);
          		criteria.add(Restrictions.eq("cname", "tom"));
          		List<Customer> list = criteria.list();*/
          		
          		// 模糊查询;
          		/*Criteria criteria = session.createCriteria(Customer.class);
          		criteria.add(Restrictions.like("cname", "t%"));
          		List<Customer> list = criteria.list();*/
          		
          		// 条件并列查询
          		Criteria criteria = session.createCriteria(Customer.class);
          		criteria.add(Restrictions.like("cname", "t%"));
          		criteria.add(Restrictions.ge("age", 35));
          		List<Customer> list = criteria.list();
          
          ```

          

        * 离线查询

          ```java
          		//web & service
          		DetachedCriteria detachedCriteria = DetachedCriteria.forClass(Customer.class);
          		detachedCriteria.add(Restrictions.eq("cid", 1));
          		
          		//---------------dao
          		
          		Session session = factory.openSession();
          		session.beginTransaction();
          		
          		// 离线Criteria 与session绑定
          		Criteria criteria = detachedCriteria.getExecutableCriteria(session);
          		List<Customer> allCustomer = criteria.list();
          		System.out.println(allCustomer.size());
          
          ```

          

* Transaction：事务对象

  * session.beginTransaction()

  * commit()
  * rollback()

### 4.Hibernate持久化对象三种状态

* 瞬时态
* 持久态
* 托管态

### 5.Hibernate级联操作：cascade

* 级联保存或更新：save-update

  ```java
  		Customer customer = new Customer();
  		customer.setCustName("凤凰");
  		
  		LinkMan linkMan1 = new LinkMan();
  		linkMan1.setLkmName("锦蜜");
  		
  		LinkMan linkMan2 = new LinkMan();
  		linkMan2.setLkmName("小淘淘");
  		
  		LinkMan linkMan3 = new LinkMan();
  		linkMan3.setLkmName("觅儿");
  		
  		customer.getLinkMans().add(linkMan1);
  		customer.getLinkMans().add(linkMan2);
  		customer.getLinkMans().add(linkMan3);
  		
  		session.save(customer);
  
  <set name="linkMans" cascade="save-update">
  ```

  

* 级联删除：delete

  ```java
  		Customer customer = session.get(Customer.class, 4);
  		
  		session.delete(customer);
  
  <set name="linkMans" cascade="delete">
  ```

  

### 6.inverse：是否放弃外键维护权（双向关联时）







