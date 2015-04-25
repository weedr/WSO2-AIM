
PRE-REQUESTIES
===============
1)WSO2 Application Server 5.2.1
2)WSO2 API Manager

INSTRUCTIONS
==============

1) Log in to the API Publisher (https://localhost:9443/publisher) and create the following APIs.

   Delivery API

        API Name= pizzaShack
        Context = /pizzashack/delivery
        Version = 1.0.0
        Production Endpoint URL=http://localhost:9765/pizzashack-api-1.0.0/api/delivery
        API Resources =Keep the default values 

   Order API
        
        API Name= pizzashack-order
        Context = /pizzashack/order
        Version = 1.0.0
        Production Endpoint URL=http://localhost:9765/pizzashack-api-1.0.0/api/order
        API Resources =Keep the default values 

   Menu API

        API Name= pizzashack-menu
        Context = /pizzashack/menu
        Version = 1.0.0
        Production Endpoint URL=http://localhost:9765/pizzashack-api-1.0.0/api/menu
        API Resources =Keep the default values 
	
2) Navigate to the Lifecycles tab of each API and promote them to PUBLISHED state.

3) Log in to the API Store (https://localhost:9443/store) and click on each API created earlier. Next, subscribe to each of them using the default application. 

4) After subscription, a message appears. Choose Go to My Subscriptions.

5) The Subscriptions page opens. Create a production key by clicking the Generate button associated with it. You also have the option to increase the default token validity period, which is 1 hour.

6) You get the access token, a consumer key and a consumer secret. Replace the consumer key and secret pair in <APIM_HOME>/samples/PizzaShack/pizza-shack-web/src/main/webapp/WEB-INF/web.xml with the newly generated ones. For example,
	
	<context-param>
	   <param-name>consumerKey</param-name>
	   <param-value>szsHscDYLeKUcwA1GhPARQlflusa</param-value>
	</context-param>
	<context-param>
	   <param-name>consumerSecret</param-name>
	   <param-value>wJEfRDE3JeFnGMuwVNseNzsXM1sa</param-value>
	</context-param>

    You now have three APIs subscribed under an application and an access token to the application. Next, we deploy a Web application in the Application Server and use it to invoke the APIs.

7) Run mvn clean install command in <APIM_HOME>/samples/PizzaShack/pizza-shack-web and <APIM_HOME>/samples/PizzaShack/pizza-shack-api to build the sample files.

8) App Server should run with port offset 2. Start WSO2 AS (https://localhost:9445/console) and log into its management console

9) Deploy <APIM_HOME>/samples/PizzaShack/pizza-shack-web/target/pizzashack.war and <APIM_HOME>/samples/PizzaShack/pizza-shack-api/target/pizzashack-api-1.0.0.war into the Application Server.

10) After deploying, access the application using http://localhost:9765/pizzashack. It opens the application in a Web browser.

11) You can use this application to order pizza. Internally, the APIs get invoked when you use the application.

