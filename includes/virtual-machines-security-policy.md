It’s important to keep your virtual machine (VM) secure for the applications that you run. Securing your VMs can include one or more Azure services and features that cover secure access to your VMs and secure storage of your data. This article provides information that enables you to keep your VM and applications secure.

## Antimalware

The modern threat landscape for cloud environments is dynamic, increasing the pressure to maintain effective protection in order to meet compliance and security requirements. [Microsoft Antimalware for Azure](../articles/security/azure-security-antimalware.md) is a free real-time protection capability that helps identify and remove viruses, spyware, and other malicious software. Alerts can be configured to notify you when known malicious or unwanted software attempts to install itself or run on your VM.

## Azure Security Center

[Azure Security Center](../articles/security-center/security-center-intro.md) helps you prevent, detect, and respond to threats to your VMs. Security Center provides integrated security monitoring and policy management across your Azure subscriptions, helps detect threats that might otherwise go unnoticed, and works with a broad ecosystem of security solutions.

## Encryption

For enhanced [Windows VM](../articles/virtual-machines/windows/encrypt-disks.md) and [Linux VM](../articles/virtual-machines/linux/encrypt-disks.md) security and compliance, virtual disks in Azure can be encrypted. Virtual disks on Windows VMs are encrypted at rest using Bitlocker. Virtual disks on Linux VMs are encrypted at rest using dm-crypt. 

There is no charge for encrypting virtual disks in Azure. Cryptographic keys are stored in Azure Key Vault using software-protection, or you can import or generate your keys in Hardware Security Modules (HSMs) certified to FIPS 140-2 level 2 standards. These cryptographic keys are used to encrypt and decrypt virtual disks attached to your VM. You retain control of these cryptographic keys and can audit their use. An Azure Active Directory service principal provides a secure mechanism for issuing these cryptographic keys as VMs are powered on and off.

## Key Vault and SSH Keys

Secrets and certificates can be modeled as resources and provided by [Key Vault](../articles/key-vault/key-vault-whatis.md). You can use Azure PowerShell to create key vaults for [Windows VMs](../articles/virtual-machines/windows/key-vault-setup.md) and the Azure CLI for [Linux VMs](../articles/virtual-machines/linux/key-vault-setup.md). You can also create keys for encryption.

Key vault access policies grant permissions to keys, secrets, and certificates separately. For example, you can give a user access to only keys, but no permissions for secrets. However, permissions to access keys or secrets or certificates are at the vault level. In other words, [key vault access policy](../articles/key-vault/key-vault-secure-your-key-vault.md) does not support object level permissions.

When you connect to VMs, you should use public-key cryptography to provide a more secure way to sign in to them. This process involves a public and private key exchange using the secure shell (SSH) command to authenticate yourself rather than a username and password. Passwords are vulnerable to brute-force attacks, especially on Internet-facing VMs such as web servers. With a secure shell (SSH) key pair, you can create a [Linux VM](../articles/virtual-machines/linux/mac-create-ssh-keys.md) that uses SSH keys for authentication, eliminating the need for passwords to log in. You can also use SSH keys to connect from a [Windows VM](../articles/virtual-machines/linux/ssh-from-windows.md) to a Linux VM.

## Policies

[Azure policies](../articles/azure-policy/azure-policy-introduction.md) can be used to define the desired behavior for your organization's [Windows VMs](../articles/virtual-machines/windows/policy.md) and [Linux VMs](../articles/virtual-machines/linux/policy.md). By using policies, an organization can enforce various conventions and rules throughout the enterprise. Enforcement of the desired behavior can help mitigate risk while contributing to the success of the organization.

## Role-based access control

Using [role-based access control (RBAC)](../articles/role-based-access-control/overview.md), you can segregate duties within your team and grant only the amount of access to users on your VM that they need to perform their jobs. Instead of giving everybody unrestricted permissions on the VM, you can allow only certain actions. You can configure access control for the VM in the [Azure portal](../articles/role-based-access-control/role-assignments-portal.md), using the [Azure CLI](https://docs.microsoft.com/cli/azure/role), or[Azure PowerShell](../articles/role-based-access-control/role-assignments-powershell.md).


## Next steps
- Walk through the steps to monitor virtual machine security by using Azure Security Center for [Linux](../articles/virtual-machines/linux/tutorial-azure-security.md) or [Windows](../articles/virtual-machines/windows/tutorial-azure-security.md).