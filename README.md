# DogFoodConf
Terraform to FreeIpa


This is talk I did at the DogFood Conference. This talk is about how to get started with Azure by using Terraform. Then we move into provisioning our instances with Ansible. The next phase will be to do this all with containers.

So lets get started

1. Make you Azure subscription 
http://observer.com/2017/10/string-of-breaches-at-nsa-reveal-security-issues-plague-agency/

2. Once in I advise you to play around with it but for now lets move into setting up Azure Command line. Plese pick your OS and meet you on Step 3.
https://docs.microsoft.com/en-us/cli/azure/install-azure-cli?view=azure-cli-latest

3.  Now you have to az login and the prompt. https://docs.microsoft.com/en-us/cli/azure/authenticate-azure-cli?view=azure-cli-latest

Once set up you do the following as examples:
az vm list-sizes --location eastus --output table | head -n 5
  MaxDataDiskCount    MemoryInMb  Name                      NumberOfCores    OsDiskSizeInMb    ResourceDiskSizeInMb
------------------  ------------  ----------------------  ---------------  ----------------  ----------------------
                 4          3584  Standard_DS1_v2                       1           1047552                    7168
                 8          7168  Standard_DS2_v2                       2           1047552                   14336
                16         14336  Standard_DS3_v2                       4           1047552                   28672

az vm list-ip-addresses --output table (this will be shown after you have creaed some instances)
VirtualMachine                   PublicIPAddresses    PrivateIPAddresses
-------------------------------  -------------------  --------------------
freeipa-client.womeninlinux.com  13.90.143.185        10.0.1.5
freeipa.womeninlinux.com         13.90.197.237        10.0.1.

4. So lets setup the service principal
https://www.terraform.io/docs/providers/azurerm/authenticating_via_service_principal.html

Please note setting up the role as OWNER is key. Also having these four credentials (needed for terraform)
subscription and tenant ids can be obtained from the portal
{
  "appId": "a487e0c1-82af-47d9-9a0b-af184eb87646d",
  "displayName": "MyDemoWebApp",
  "name": "http://MyDemoWebApp",
  "password": {strong password},
  "tenant": "XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX"
}

Okay so we need to install Terraform. Please pick your OS.
https://www.terraform.io/downloads.html

5. Now its time to TERRAFORM. You will need the credentials in Step 4 in your .tf file or place them ~/.azure/credentials
This is something to get you started
https://www.terraform.io/intro/getting-started/build.html

I have attached the files I used for my talk. You can change them according to your infrastructure




