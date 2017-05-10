# SpringMVC3
handlerMapping

几种方式找到controller

1.通过beanname找到controller：org.springframework.web.servlet.mvc.support.ControllerBeanNameHandlerMapping
例如：user.jsp   （user.do）

	<a href="user.do">根据beanname访问controller</a>

web.xml

	<servlet>
    <servlet-name>springmvc</servlet-name>
    <servlet-class>org.springframework.web.servlet.DispatcherServlet</servlet-class>
  	</servlet>
  	<servlet-mapping>
    <servlet-name>springmvc</servlet-name>
    <url-pattern>*.do</url-pattern>
  	</servlet-mapping>

springmvc-servlet.xml

	<bean class="org.springframework.web.servlet.mvc.support.ControllerBeanNameHandlerMapping"></bean>
	<bean name="user.do" class="controller.UserController"></bean>

2.根据简单url来查找controller	（userInfo.do）

	<bean class="org.springframework.web.servlet.handler.SimpleUrlHandlerMapping">
		<property name="mappings">
			<props>
				<prop key="/userInfo.do">useController</prop>
			</props>
		</property>
	</bean>
	<bean id="useController" name="user.do" class="controller.UserController"></bean>
	
3.根据控制类的类名访问controller，访问时类名首字母需要小写 (userController.do)
	
	<!-- 控制类的类名访问controller -->
	<bean class="org.springframework.web.servlet.mvc.support.ControllerClassNameHandlerMapping"></bean>
	<bean class="controller.UserController"></bean>
		  	
	  	