---
title: "C&#243;mo: Configurar el comportamiento del mensaje relativo a la confianza de ClickOnce | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "aplicaciones ClickOnce, instalar sin preguntar"
  - "aplicaciones ClickOnce, mensaje relativo a la confianza"
  - "implementación ClickOnce, instalar sin preguntar"
  - "implementación ClickOnce, mensaje relativo a la confianza"
  - "implementar aplicaciones [ClickOnce], mensaje relativo a la confianza"
ms.assetid: cc04fa75-012b-47c9-9347-f4216be23cf2
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# C&#243;mo: Configurar el comportamiento del mensaje relativo a la confianza de ClickOnce
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede configurar el mensaje de ClickOnce relativo a la confianza para controlar si a los usuarios finales se les ofrece la opción de instalar aplicaciones ClickOnce, como aplicaciones Windows Forms, aplicaciones Windows Presentation Foundation, aplicaciones de consola, aplicaciones de explorador WPF y soluciones de Office.  Para configurar el mensaje relativo a la confianza, establezca las claves del Registro en el equipo de cada usuario final.  
  
 En la tabla siguiente se muestran las opciones de configuración que se pueden aplicar a cada una de los cinco zonas \(Internet, UntrustedSites, MyComputer, LocalIntranet y TrustedSites\).  
  
|Opción|Valor de configuración del Registro|Descripción|  
|------------|-----------------------------------------|-----------------|  
|Habilitar el mensaje relativo a la confianza.|`Enabled`|El mensaje de ClickOnce relativo a la confianza se muestra para que los usuarios finales puedan otorgar confianza a las aplicaciones ClickOnce.|  
|Restringir el mensaje relativo a la confianza.|`AuthenticodeRequired`|El mensaje de ClickOnce relativo a la confianza solo se muestra si las aplicaciones ClickOnce se firman con un certificado que identifica al publicador.|  
|Deshabilitar el mensaje relativo a la confianza.|`Disabled`|El mensaje de ClickOnce relativo a la confianza no se muestra en ninguna aplicación ClickOnce que no esté firmada con un certificado de confianza explícito.|  
  
 En la tabla siguiente se muestra el comportamiento predeterminado de cada zona.  La columna Aplicaciones hace referencia a las aplicaciones Windows Forms, a las aplicaciones Windows Presentation Foundation, a las aplicaciones de explorador WPF y a las aplicaciones de consola.  
  
|Zona|Aplicaciones|Soluciones de Office|  
|----------|------------------|--------------------------|  
|`MyComputer`|`Enabled`|`Enabled`|  
|`LocalIntranet`|`Enabled`|`Enabled`|  
|`TrustedSites`|`Enabled`|`Enabled`|  
|`Internet`|`Enabled`|`AuthenticodeRequired`|  
|`UntrustedSites`|`Disabled`|`Disabled`|  
  
 Para invalidar estos valores, habilite, restrinja o deshabilite el mensaje de ClickOnce relativo a la confianza.  
  
## Habilitar el mensaje de ClickOnce relativo a la confianza  
 Si desea que a los usuarios finales se les ofrezca la opción de instalar y ejecutar cualquier aplicación ClickOnce que provenga de una zona determinada, habilite el mensaje relativo a la confianza de dicha zona.  
  
#### Para habilitar el mensaje de ClickOnce relativo a la confianza mediante el editor del Registro  
  
1.  Abra el editor del Registro:  
  
    1.  Haga clic en **Inicio** y, a continuación, haga clic en **Ejecutar**.  
  
    2.  En el cuadro **Abrir**, escriba `regedit32` y, a continuación, haga clic en **Aceptar**.  
  
2.  Busque la siguiente clave del Registro:  
  
     \\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel  
  
     Si la clave no existe, créela.  
  
3.  Agregue las subclaves siguientes como **Valor de cadena**, si no existen ya, junto con los valores asociados que se muestran en la tabla siguiente.  
  
    |Subclave de valor alfanumérico|Valor|  
    |------------------------------------|-----------|  
    |`Internet`|`Enabled`|  
    |`UntrustedSites`|`Disabled`|  
    |`MyComputer`|`Enabled`|  
    |`LocalIntranet`|`Enabled`|  
    |`TrustedSites`|`Enabled`|  
  
     En las soluciones de Office, `Internet` tiene el valor predeterminado `AuthenticodeRequired` y `UntrustedSites` tiene el valor `Disabled`.  En todas las demás, `Internet` tiene el valor predeterminado `Enabled`.  
  
#### Para habilitar el mensaje de ClickOnce relativo a la confianza mediante programación  
  
1.  Cree una aplicación de consola de Visual Basic o Visual C\# en Visual Studio.  
  
2.  Abra el archivo Program.vb o Program.cs para modificarlo y agregue el código siguiente.  
  
    ```vb#  
    Dim key As Microsoft.Win32.RegistryKey  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")  
    key.SetValue("MyComputer", "Enabled")  
    key.SetValue("LocalIntranet", "Enabled")  
    key.SetValue("Internet", "Enabled")  
    key.SetValue("TrustedSites", "Enabled")  
    key.SetValue("UntrustedSites", "Disabled")  
    key.Close()  
    ```  
  
    ```c#  
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
  
## Restringir el mensaje de ClickOnce relativo a la confianza  
 Restrinja el mensaje relativo a la confianza para que sea necesario firmar las soluciones con certificados Authenticode que dispongan de una identidad conocida antes de que se pida a los usuarios una decisión relativa a la confianza.  
  
#### Para restringir el mensaje de ClickOnce relativo a la confianza mediante el editor del Registro  
  
1.  Abra el editor del Registro:  
  
    1.  Haga clic en **Inicio** y, a continuación, haga clic en **Ejecutar**.  
  
    2.  En el cuadro **Abrir**, escriba `regedit` y, a continuación, haga clic en **Aceptar**.  
  
2.  Busque la siguiente clave del Registro:  
  
     \\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel  
  
     Si la clave no existe, créela.  
  
3.  Agregue las subclaves siguientes como **Valor de cadena**, si no existen ya, junto con los valores asociados que se muestran en la tabla siguiente.  
  
    |Subclave de valor alfanumérico|Valor|  
    |------------------------------------|-----------|  
    |`UntrustedSites`|`Disabled`|  
    |`Internet`|`AuthenticodeRequired`|  
    |`MyComputer`|`AuthenticodeRequired`|  
    |`LocalIntranet`|`AuthenticodeRequired`|  
    |`TrustedSites`|`AuthenticodeRequired`|  
  
#### Para restringir el mensaje de ClickOnce relativo a la confianza mediante programación  
  
1.  Cree una aplicación de consola de Visual Basic o Visual C\# en Visual Studio.  
  
2.  Abra el archivo Program.vb o Program.cs para modificarlo y agregue el código siguiente.  
  
    ```vb#  
    Dim key As Microsoft.Win32.RegistryKey  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")  
    key.SetValue("MyComputer", "AuthenticodeRequired")  
    key.SetValue("LocalIntranet", "AuthenticodeRequired")  
    key.SetValue("Internet", "AuthenticodeRequired")  
    key.SetValue("TrustedSites", "AuthenticodeRequired")  
    key.SetValue("UntrustedSites", "Disabled")  
    key.Close()  
    ```  
  
    ```c#  
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
  
## Deshabilitar el mensaje de ClickOnce relativo a la confianza  
 Puede deshabilitar el mensaje relativo a la confianza para que a los usuarios finales no se les ofrezca la opción de instalar soluciones en cuya directiva de seguridad aún no confían.  
  
#### Para deshabilitar el mensaje de ClickOnce relativo a la confianza mediante el editor del Registro  
  
1.  Abra el editor del Registro:  
  
    1.  Haga clic en **Inicio** y, a continuación, haga clic en **Ejecutar**.  
  
    2.  En el cuadro **Abrir**, escriba `regedit` y, a continuación, haga clic en **Aceptar**.  
  
2.  Busque la siguiente clave del Registro:  
  
     \\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel  
  
     Si la clave no existe, créela.  
  
3.  Agregue las subclaves siguientes como **Valor de cadena**, si no existen ya, junto con los valores asociados que se muestran en la tabla siguiente.  
  
    |Subclave de valor alfanumérico|Valor|  
    |------------------------------------|-----------|  
    |`UntrustedSites`|`Disabled`|  
    |`Internet`|`Disabled`|  
    |`MyComputer`|`Disabled`|  
    |`LocalIntranet`|`Disabled`|  
    |`TrustedSites`|`Disabled`|  
  
#### Para deshabilitar el mensaje de ClickOnce relativo a la confianza mediante programación  
  
1.  Cree una aplicación de consola de Visual Basic o Visual C\# en Visual Studio.  
  
2.  Abra el archivo Program.vb o Program.cs para modificarlo y agregue el código siguiente.  
  
    ```vb#  
    Dim key As Microsoft.Win32.RegistryKey  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")  
    key.SetValue("MyComputer", "Disabled")  
    key.SetValue("LocalIntranet", "Disabled")  
    key.SetValue("Internet", "Disabled")  
    key.SetValue("TrustedSites", "Disabled")  
    key.SetValue("UntrustedSites", "Disabled")  
    key.Close()  
    ```  
  
    ```c#  
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
  
## Vea también  
 [Proteger las aplicaciones ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Seguridad de acceso del código para aplicaciones ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [ClickOnce y Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Información general sobre la implementación de aplicaciones de confianza](../deployment/trusted-application-deployment-overview.md)   
 [Cómo: Habilitar la configuración de seguridad para aplicaciones ClickOnce](../deployment/how-to-enable-clickonce-security-settings.md)   
 [Cómo: Establecer una zona de seguridad para una aplicación ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [Cómo: Establecer permisos personalizados para una aplicación ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Cómo: Depurar una aplicación ClickOnce con permisos restringidos](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [Cómo: Agregar un publicador de confianza a un equipo cliente para aplicaciones ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)   
 [Cómo: Volver a firmar manifiestos de aplicación e implementación](../deployment/how-to-re-sign-application-and-deployment-manifests.md)