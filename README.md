# terraform-choco
```
resource "azurerm_virtual_machine_extension" "choco2" {
  name                       = "install-choco2"
  virtual_machine_id         = azurerm_windows_virtual_machine.vishalvm.id
  publisher                  = "Microsoft.Compute"
  type                       = "CustomScriptExtension
  type_handler_version       = "1.10"
  auto_upgrade_minor_version = true

  settings = <<SETTINGS
    {
      "fileUris": [
        "https://community.chocolatey.org/install.ps1"
      ]
    }
  SETTINGS

  protected_settings = <<PROTECTED_SETTINGS
    {
      "commandToExecute": "powershell.exe -ExecutionPolicy Unrestricted -command ./install.ps1; choco install boxstarter -y "
    }
  PROTECTED_SETTINGS

}
```
