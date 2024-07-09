# Dynamic_Routing_For_MicroServices_Using_Application_Gateway

Provisioned the Application Gateway on Azure Cloud to handle the traffic for different micro-services.

![image](https://github.com/samirwadkar31/Dynamic_Routing_For_MicroServices_Using_Application_Gateway/assets/74359548/facc3490-9de1-429d-a57d-21f803d46562)

Created below three backend pools,

### sameer-default-page-backend :<br>
This is default pool. This contains home page. when we type **application_gateway_ip_address** in the browser, we get the response from this backend pool.

### sameer-products-backend:<br>
This backend pool contains the virtual machines, which has the code base of products microservice. When we type **application_gateway_ip_address/products** in the browser, application gatway redirects this request to products backend pool VMs to get the desired response.

### sameer-payments-backend:<br>
This backend pool contains the virtual machines, which has the code base of payments microservice. When we type **application_gateway_ip_address/payments** in the browser, application gatway redirects this request to payments backend pool VMs to get the desired response. 

For this project, I have created 3 Ubuntu VM's and have added one VM in each backend pool. Each backend pool contains one VM with it's respective microservice code base configured with Apache2 web server.

![image](https://github.com/samirwadkar31/Dynamic_Routing_For_MicroServices_Using_Application_Gateway/assets/74359548/b5eca04c-ece9-40c6-ba47-dd0752f8151f)

We can add VMs, VMSS, Availibality sets, On-premises VMS, Specific ip address or domain names in backend pools of Application Gateway. It also has WAF, Web Application Firewall, which enhances the security of our applications.<br>
<br>

Have created http listener wich listens on http port 80. You can create for https port 443, custom ports like 8089 etc as per the requirement. 

![image](https://github.com/samirwadkar31/Dynamic_Routing_For_MicroServices_Using_Application_Gateway/assets/74359548/159346d5-2627-4105-b182-70cf4d98bc78)

Have created the backend setting which talks to backend pool vms on port 80

![image](https://github.com/samirwadkar31/Dynamic_Routing_For_MicroServices_Using_Application_Gateway/assets/74359548/507b6b71-1c45-4ee8-bb38-c520eed9a802)

Now, main part - path based routing rules:

![image](https://github.com/samirwadkar31/Dynamic_Routing_For_MicroServices_Using_Application_Gateway/assets/74359548/301350fc-0773-4551-aadc-1e0c32c3af6f)

When user clicks on application-gate-way-public-ip-address, it returns the response from the backend pool which we have mentioned here as a default. Hence, I have created one sameer-default-page-backend pool where, I have stored home page code.

![image](https://github.com/samirwadkar31/Dynamic_Routing_For_MicroServices_Using_Application_Gateway/assets/74359548/291cba40-1650-46ef-9adf-6c218350b97d)

![image](https://github.com/samirwadkar31/Dynamic_Routing_For_MicroServices_Using_Application_Gateway/assets/74359548/288a3bcb-c186-46df-a945-58b3377fc189)

Application gateway uses these rules to manage and distribute the traffic across differnt backend pools/ microservices.

Let's put **application_gateway_ip_address** in the browser, <br>

It has directed this request to sameer-default-page-backend pool VM.

![image](https://github.com/samirwadkar31/Dynamic_Routing_For_MicroServices_Using_Application_Gateway/assets/74359548/a0c8bb49-ebaf-4093-ae4c-7a13d72b84fa)

Let's click on products button and see, where the application gatway directs us,<br>

Beacuse of this routing rule /products* , application gateway has directed us to sameer-products-backend pool where our products code base is present.

![image](https://github.com/samirwadkar31/Dynamic_Routing_For_MicroServices_Using_Application_Gateway/assets/74359548/9b167930-634a-4d5d-b5de-89654c30e369)

Let's click on payments button and see, where the application gatway directs us,<br>

Beacuse of this routing rule /payments* , application gateway has directed us to sameer-payments-backend pool where our payments code base is present.

![image](https://github.com/samirwadkar31/Dynamic_Routing_For_MicroServices_Using_Application_Gateway/assets/74359548/a1191081-76fc-4ee2-ad93-b3fee357a7a7)
