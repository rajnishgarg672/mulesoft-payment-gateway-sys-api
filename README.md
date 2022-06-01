# mulesoft-payment-gateway-sys-api
 

+ [Use Case](#usecase)
+ [Considerations](#considerations)
	* [APIs security considerations](#apissecurityconsiderations)
+ [Run it!](#runit)
	* [Running on Studio](#runonstudio)
	* [Running on CloudHub](#runoncloudhub)
	* [Note](#RequiredDetailstorunonlocalandcloudhub)
	


# Use Case <a name="usecase"/>

As a Customer I want to simulate checkout experience by interacting with payment gateway.mulesoft-payment-gateway-sys-api is system api being called by mulesoft-shoppingcart-process-api after shopping cart id is generated.This is just a dummy api validates the card details against the payment master file stored within api itself.

### POST/payment
This endpoint will trigger subflow implementation-logic which validates the card details along with amount against the payment master file stored in api and makes decision to reject or approve the transaction.

 

# Considerations <a name="considerations"/>

To run this api in local enviroment, there are certain preconditions that must be considered. **Failling to do so could lead to unexpected behavior of the api.**

## APIs security considerations <a name="apissecurityconsiderations"/>
This system API is  deployed to CloudHub and managed using the API Platform Manager.
   

# Run it! <a name="runit"/>
Simple steps to get mulesoft-payment-gateway-sys-api running.
See below.


### Where to Download Mule Studio and Mule ESB
Here are few tips to download Anypoint Studio.

+ You can download Mule Studio from this [Location](https://www.mulesoft.com/lp/dl/studio)


### Importing an mulesoft-payment-gateway-sys-api into Studio
Anypoint Studio offers several ways to import a project into the workspace, for example: 

+ Anypoint Studio Project from File System
+ Packaged mule application (.jar)


### Running on Studio <a name="runonstudio"/>
Once you have imported  mulesoft-payment-gateway-sys-api into Anypoint Studio you need to follow these steps to run it:

+ Locate the properties file `mulesoft-payment-gateway-sys-api-<env>.yaml`, in src/main/mule/resources as we need to decrypt any credetials using masterKey
+ Once that is done, right click on your Anypoint mulesoft-payment-gateway-sys-api project folder 
+ Hover you mouse over `"Run as"`
+ Click on  `"Mule Application(configure)"`.
+ Click on Enviromet tab.
+ click on Add.
+ Set new environment variable as "Name" : env and "Value" : sandbox
+ Set new environment variable as "Name" : masterKey and "Value" : *********************************
+ Click on Arguments tab and type -Danypoint.platform.gatekeeper=disabled and apply. for disabling the auto discovery.


## Running on CloudHub <a name="runoncloudhub"/>
After deploying it to cloudhub, You need to go to `"Manage Application"` > `"Properties"` to set all environment variables detailed in **Properties to be configured**.

anypoint.platform.client_id=*********************************
anypoint.platform.base_url=https://anypoint.mulesoft.com/
anypoint.platform.analytics_base_url=https://analytics-ingest.anypoint.mulesoft.com
masterKey=*********************************
anypoint.platform.client_secret=*********************************
anypoint.platform.config.analytics.agent.enabled=false
env=sandbox

## Note <a name="RequiredDetailstorunonlocalandcloudhub"/>
Please refer Rajnish_ShoppingCart_project.pdf for details on masterKey as well as other credetails required to run in local as well as on cloudhub
