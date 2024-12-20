# VM-AZURE
 That is documentacion about VM in Azure

That is ARM tamplet VM for use that file please create template.jonson

    {
        "$schema": "https://schema.management.azure.com/schemas/2019-04-01/deploymentTemplate.json#",
        "contentVersion": "1.0.0.0",
        "parameters": {
            "virtualMachines_my_first_vm_name": {
                "defaultValue": "my-first-vm",
                "type": "String"
            },
            "disks_my_first_vm_OsDisk_1_5d18ffa6418b455c8fa8001c12707b82_externalid": {
                "defaultValue": "/subscriptions/7f52d7c8-453d-4535-9603-3ae49813fdc1/resourceGroups/my_resource/providers/Microsoft.Compute/disks/my-first-vm_OsDisk_1_5d18ffa6418b455c8fa8001c12707b82",
                "type": "String"
            },
            "networkInterfaces_my_nic_int_externalid": {
                "defaultValue": "/subscriptions/7f52d7c8-453d-4535-9603-3ae49813fdc1/resourceGroups/my_resource/providers/Microsoft.Network/networkInterfaces/my_nic_int",
                "type": "String"
            }
        },
        "variables": {},
        "resources": [
            {
                "type": "Microsoft.Compute/virtualMachines",
                "apiVersion": "2024-07-01",
                "name": "[parameters('virtualMachines_my_first_vm_name')]",
                "location": "eastus",
                "properties": {
                    "hardwareProfile": {
                        "vmSize": "Standard_B1s"
                    },
                    "storageProfile": {
                        "imageReference": {
                            "publisher": "MicrosoftWindowsServer",
                            "offer": "WindowsServer",
                            "sku": "2016-Datacenter",
                            "version": "latest"
                        },
                        "osDisk": {
                            "osType": "Windows",
                            "name": "[concat(parameters('virtualMachines_my_first_vm_name'), '_OsDisk_1_5d18ffa6418b455c8fa8001c12707b82')]",
                            "createOption": "FromImage",
                            "caching": "ReadWrite",
                            "writeAcceleratorEnabled": false,
                            "managedDisk": {
                                "storageAccountType": "Standard_LRS",
                                "id": "[parameters('disks_my_first_vm_OsDisk_1_5d18ffa6418b455c8fa8001c12707b82_externalid')]"
                            },
                            "deleteOption": "Detach",
                            "diskSizeGB": 127
                        },
                        "dataDisks": []
                    },
                    "osProfile": {
                        "computerName": "[parameters('virtualMachines_my_first_vm_name')]",
                        "adminUsername": "user.admin",
                        "windowsConfiguration": {
                            "provisionVMAgent": true,
                            "enableAutomaticUpdates": true,
                            "patchSettings": {
                                "patchMode": "AutomaticByOS",
                                "assessmentMode": "ImageDefault",
                                "enableHotpatching": false
                            },
                            "winRM": {
                                "listeners": []
                            }
                        },
                        "secrets": [],
                        "allowExtensionOperations": true,
                        "requireGuestProvisionSignal": true
                    },
                    "networkProfile": {
                        "networkInterfaces": [
                            {
                                "id": "[parameters('networkInterfaces_my_nic_int_externalid')]",
                                "properties": {
                                    "primary": true
                                }
                            }
                        ]
                    },
                    "diagnosticsProfile": {
                        "bootDiagnostics": {
                            "enabled": false
                        }
                    },
                    "priority": "Regular",
                    "extensionsTimeBudget": "PT1H30M"
                }
            }
        ]
    }





# USE TEMPLATE 

go to vm

![alt text](IMAGE/image.png)

go to automatisacion / export tamplet

![alt text](IMAGE/image1.png)

click deploy  

![alt text](IMAGE/image2.png)

and go to remember about two file parameters and tamplet

![alt text](IMAGE/image3.png)

next click add file

![alt text](IMAGE/image4.png)

