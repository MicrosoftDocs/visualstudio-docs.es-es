---
title: 'Cómo: configurar el comportamiento de solicitud de la confianza de ClickOnce | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, install without prompting
- deploying applications [ClickOnce], trust prompt
- ClickOnce applications, install without prompting
- ClickOnce applications, trust prompt
- ClickOnce deployment, trust prompt
ms.assetid: cc04fa75-012b-47c9-9347-f4216be23cf2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d37e5fa465a5e19b1bfb7577f6ab06c61782f775
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
ms.locfileid: "31561560"
---
# <a name="how-to-configure-the-clickonce-trust-prompt-behavior"></a>Cómo: Configurar el comportamiento del mensaje relativo a la confianza de ClickOnce
Puede configurar el aviso de confianza de ClickOnce para controlar si los usuarios finales tienen la opción de instalar aplicaciones ClickOnce, como aplicaciones de Windows Forms, aplicaciones de Windows Presentation Foundation, aplicaciones de consola, explorador WPF las aplicaciones y soluciones de Office. Configurar el aviso de confianza mediante el establecimiento de las claves del registro en el equipo de cada usuario final.  
  
 En la tabla siguiente se muestra las opciones de configuración que se pueden aplicar a cada una de las cinco zonas (Internet, UntrustedSites, MyComputer, intranet local y TrustedSites).  
  
|Opción|Valor de la configuración del registro|Descripción|  
|------------|----------------------------|-----------------|  
|Habilitar el aviso de confianza.|`Enabled`|El aviso de confianza de ClickOnce es la pantalla para que los usuarios finales pueden conceder confianza a las aplicaciones de ClickOnce.|  
|Restringir el aviso de confianza.|`AuthenticodeRequired`|El aviso de confianza de ClickOnce solo se muestra si las aplicaciones ClickOnce se firman con un certificado que identifique al publicador.|  
|Deshabilitar el aviso de confianza.|`Disabled`|No se muestra el aviso de confianza de ClickOnce para las aplicaciones ClickOnce que no están firmadas con un certificado de confianza explícita.|  
  
 En la tabla siguiente se muestra el comportamiento predeterminado para cada zona. La columna aplicaciones hace referencia a las aplicaciones de Windows Forms, aplicaciones de Windows Presentation Foundation, aplicaciones de explorador WPF y las aplicaciones de consola.  
  
|Zona|Aplicaciones|soluciones de Office|  
|----------|------------------|----------------------|  
|`MyComputer`|`Enabled`|`Enabled`|  
|`LocalIntranet`|`Enabled`|`Enabled`|  
|`TrustedSites`|`Enabled`|`Enabled`|  
|`Internet`|`Enabled`|`AuthenticodeRequired`|  
|`UntrustedSites`|`Disabled`|`Disabled`|  
  
 Puede habilitar o deshabilitar el aviso de confianza de ClickOnce o restringir para invalidar estos valores.  
  
## <a name="enabling-the-clickonce-trust-prompt"></a>Habilitar el aviso de confianza de ClickOnce  
 Habilitar el aviso de confianza para una zona cuando desee que los usuarios finales se mostrará la opción de instalar y ejecutar las aplicaciones ClickOnce que proceden de esa zona.  
  
#### <a name="to-enable-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Para habilitar el aviso de confianza de ClickOnce mediante el editor del registro  
  
1.  Abra el editor del registro:  
  
    1.  Haga clic en **iniciar**y, a continuación, haga clic en **ejecutar**.  
  
    2.  En el **abiertos** , escriba `regedit32`y, a continuación, haga clic en **Aceptar**.  
  
2.  Busque la siguiente clave del registro:  
  
     \HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\. NETFramework\Security\TrustManager\PromptingLevel  
  
     Si la clave no existe, créela.  
  
3.  Agregue las subclaves siguientes como **valor de cadena**, si no existe ya, con los valores asociados que se muestra en la tabla siguiente.  
  
    |Subclave del valor de cadena|Valor|  
    |-------------------------|-----------|  
    |`Internet`|`Enabled`|  
    |`UntrustedSites`|`Disabled`|  
    |`MyComputer`|`Enabled`|  
    |`LocalIntranet`|`Enabled`|  
    |`TrustedSites`|`Enabled`|  
  
     Para las soluciones de Office, `Internet` tiene el valor predeterminado `AuthenticodeRequired` y `UntrustedSites` tiene el valor `Disabled`. Para todos los demás, `Internet` tiene el valor predeterminado `Enabled`.  
  
#### <a name="to-enable-the-clickonce-trust-prompt-programmatically"></a>Para habilitar el aviso de confianza de ClickOnce mediante programación  
  
1.  Cree una aplicación de consola de Visual Basic o Visual C# en Visual Studio.  
  
2.  Abra el archivo Program.vb o Program.cs para modificarlo y agregue el código siguiente.  
  
    ```vb  
    Dim key As Microsoft.Win32.RegistryKey  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")  
    key.SetValue("MyComputer", "Enabled")  
    key.SetValue("LocalIntranet", "Enabled")  
    key.SetValue("Internet", "Enabled")  
    key.SetValue("TrustedSites", "Enabled")  
    key.SetValue("UntrustedSites", "Disabled")  
    key.Close()  
    ```  
  
    ```csharp  
    Microsoft.Win32.RegistryKey key;  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel");  
    key.SetValue("MyComputer", "Enabled");  
    key.SetValue("LocalIntranet", "Enabled");  
    key.SetValue("Internet", "AuthenticodeRequired");  
    key.SetValue("TrustedSites", "Enabled");  
    key.SetValue("UntrustedSites", "Disabled");  
    key.Close();  
    ```  
  
3.  Compile y ejecute la aplicación.  
  
## <a name="restricting-the-clickonce-trust-prompt"></a>Restringir el aviso de confianza de ClickOnce  
 Restringir el aviso de confianza de modo que las soluciones se deben firmar con certificados Authenticode que dispongan de una identidad conocida antes de que se piden a los usuarios una decisión de confianza.  
  
#### <a name="to-restrict-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Para restringir el aviso de confianza de ClickOnce mediante el editor del registro  
  
1.  Abra el editor del registro:  
  
    1.  Haga clic en **iniciar**y, a continuación, haga clic en **ejecutar**.  
  
    2.  En el **abiertos** , escriba `regedit`y, a continuación, haga clic en **Aceptar**.  
  
2.  Busque la siguiente clave del registro:  
  
     \HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\. NETFramework\Security\TrustManager\PromptingLevel  
  
     Si la clave no existe, créela.  
  
3.  Agregue las subclaves siguientes como **valor de cadena**, si no existe ya, con los valores asociados que se muestra en la tabla siguiente.  
  
    |Subclave del valor de cadena|Valor|  
    |-------------------------|-----------|  
    |`UntrustedSites`|`Disabled`|  
    |`Internet`|`AuthenticodeRequired`|  
    |`MyComputer`|`AuthenticodeRequired`|  
    |`LocalIntranet`|`AuthenticodeRequired`|  
    |`TrustedSites`|`AuthenticodeRequired`|  
  
#### <a name="to-restrict-the-clickonce-trust-prompt-programmatically"></a>Para restringir el aviso de confianza de ClickOnce mediante programación  
  
1.  Cree una aplicación de consola de Visual Basic o Visual C# en Visual Studio.  
  
2.  Abra el archivo Program.vb o Program.cs para modificarlo y agregue el código siguiente.  
  
    ```vb  
    Dim key As Microsoft.Win32.RegistryKey  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")  
    key.SetValue("MyComputer", "AuthenticodeRequired")  
    key.SetValue("LocalIntranet", "AuthenticodeRequired")  
    key.SetValue("Internet", "AuthenticodeRequired")  
    key.SetValue("TrustedSites", "AuthenticodeRequired")  
    key.SetValue("UntrustedSites", "Disabled")  
    key.Close()  
    ```  
  
    ```csharp  
    Microsoft.Win32.RegistryKey key;  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel");  
    key.SetValue("MyComputer", "AuthenticodeRequired");  
    key.SetValue("LocalIntranet", "AuthenticodeRequired");  
    key.SetValue("Internet", "AuthenticodeRequired");  
    key.SetValue("TrustedSites", "AuthenticodeRequired");  
    key.SetValue("UntrustedSites", "Disabled");  
    key.Close();  
    ```  
  
3.  Compile y ejecute la aplicación.  
  
## <a name="disabling-the-clickonce-trust-prompt"></a>Deshabilitar el aviso de confianza de ClickOnce  
 Puede deshabilitar el aviso de confianza para que los usuarios finales no tienen la opción para instalar soluciones que no son de confianza ya en su directiva de seguridad.  
  
#### <a name="to-disable-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Para deshabilitar el aviso de confianza de ClickOnce mediante el editor del registro  
  
1.  Abra el editor del registro:  
  
    1.  Haga clic en **iniciar**y, a continuación, haga clic en **ejecutar**.  
  
    2.  En el **abiertos** , escriba `regedit`y, a continuación, haga clic en **Aceptar**.  
  
2.  Busque la siguiente clave del registro:  
  
     \HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\. NETFramework\Security\TrustManager\PromptingLevel  
  
     Si la clave no existe, créela.  
  
3.  Agregue las subclaves siguientes como **valor de cadena**, si no existe ya, con los valores asociados que se muestra en la tabla siguiente.  
  
    |Subclave del valor de cadena|Valor|  
    |-------------------------|-----------|  
    |`UntrustedSites`|`Disabled`|  
    |`Internet`|`Disabled`|  
    |`MyComputer`|`Disabled`|  
    |`LocalIntranet`|`Disabled`|  
    |`TrustedSites`|`Disabled`|  
  
#### <a name="to-disable-the-clickonce-trust-prompt-programmatically"></a>Para deshabilitar el aviso de confianza de ClickOnce mediante programación  
  
1.  Cree una aplicación de consola de Visual Basic o Visual C# en Visual Studio.  
  
2.  Abra el archivo Program.vb o Program.cs para modificarlo y agregue el código siguiente.  
  
    ```vb  
    Dim key As Microsoft.Win32.RegistryKey  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")  
    key.SetValue("MyComputer", "Disabled")  
    key.SetValue("LocalIntranet", "Disabled")  
    key.SetValue("Internet", "Disabled")  
    key.SetValue("TrustedSites", "Disabled")  
    key.SetValue("UntrustedSites", "Disabled")  
    key.Close()  
    ```  
  
    ```csharp  
    Microsoft.Win32.RegistryKey key;  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel");  
    key.SetValue("MyComputer", "Disabled");  
    key.SetValue("LocalIntranet", "Disabled");  
    key.SetValue("Internet", "Disabled");  
    key.SetValue("TrustedSites", "Disabled");  
    key.SetValue("UntrustedSites", "Disabled");  
    key.Close();  
  
    ```  
  
3.  Compile y ejecute la aplicación.  
  
## <a name="see-also"></a>Vea también  
 [Proteger las aplicaciones ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Seguridad de acceso del código para aplicaciones ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [ClickOnce y Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Introducción a la implementación de aplicaciones de confianza](../deployment/trusted-application-deployment-overview.md)   
 [Cómo: Habilitar la configuración de seguridad de ClickOnce](../deployment/how-to-enable-clickonce-security-settings.md)   
 [Cómo: Establecer una zona de seguridad para una aplicación ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [Cómo: Establecer permisos personalizados para una aplicación ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Cómo: Depurar una aplicación ClickOnce con permisos restringidos](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [Cómo: agregar un publicador de confianza a un equipo cliente para aplicaciones ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)   
 [Cómo: Volver a firmar manifiestos de aplicación e implementación](../deployment/how-to-re-sign-application-and-deployment-manifests.md)