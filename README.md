# Dynamic_Routing_For_MicroServices_Using_Application_Gateway

Provisioned the Application Gateway on Azure Cloud to handle the traffic for differen microservices.

![image](https://github.com/samirwadkar31/Dynamic_Routing_For_MicroServices_Using_Application_Gateway/assets/74359548/facc3490-9de1-429d-a57d-21f803d46562)

Created below three backend pools,

### sameer-default-page-backend :<br>
This is default pool. This contains home page. when we type **application_gateway_ip_address** in the browser, we get the response from this backend pool.

### sameer-products-backend:<br>
This backend pool contains the virtual machines, which has the code base of products microservice. When we type **application_gateway_ip_address/products** in the browser, application gatway redirects this request to products backend pool VMs to get the desired response.

### sameer-payments-backend:<br>
This backend pool contains the virtual machines, which has the code base of payments microservice. When we type **application_gateway_ip_address/payments** in the browser, application gatway redirects this request to payments backend pool VMs to get the desired response. 

![image](https://github.com/samirwadkar31/Dynamic_Routing_For_MicroServices_Using_Application_Gateway/assets/74359548/b5eca04c-ece9-40c6-ba47-dd0752f8151f)

For this project, I have created 3 Ubuntu VM's and have added one VM in each backend pool. Each backend pool contains one VM with it's respective microservice code base configured with Apache2 web server.



