---
title: "C&#243;mo: Configurar la seguridad de la lista de inclusi&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "listas de inclusión [desarrollo de Office en Visual Studio]"
  - "permisos [desarrollo de Office en Visual Studio]"
ms.assetid: 0609d8f0-4630-4e17-aeb3-14f3134165cf
caps.latest.revision: 26
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 25
---
# C&#243;mo: Configurar la seguridad de la lista de inclusi&#243;n
  Si tiene permisos de administrador, puede configurar la confirmación de confianza de [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] de modo que controle si a los usuarios finales se les ofrece la opción de instalar soluciones de Office al guardar una decisión de confianza en la lista de inclusión.  Para obtener información sobre las listas de inclusión, vea [Otorgar confianza a las soluciones de Office mediante listas de inclusión](../vsto/trusting-office-solutions-by-using-inclusion-lists.md).  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Para las soluciones que están en cada una de las cinco zonas, puede establecer las opciones siguientes:  
  
-   Habilitar la clave del mensaje relativo a la confianza de [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] y la lista de inclusión.  Puede permitir a los usuarios finales conceder confianza a las soluciones de Office que se firman con cualquier certificado.  
  
-   Restringir la clave del mensaje relativo a la confianza de [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] y la lista de inclusión.  Puede permitir a los usuarios finales instalar soluciones de Office firmadas con un certificado que identifica al editor, pero que aún no es de confianza.  
  
-   Deshabilitar la clave del mensaje relativo a la confianza de [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] y la lista de inclusión.  Puede impedir que los usuarios finales instalen cualquier solución de Office que no esté firmada con un certificado de confianza explícita.  
  
## Habilitar la lista de inclusión  
 Si desea que a los usuarios finales se les ofrezca la opción de instalar y ejecutar cualquier solución de Office que provenga de una zona determinada, habilite la lista de inclusión de dicha zona.  
  
#### Para habilitar la lista de inclusión con el editor del Registro  
  
1.  Abra el editor del Registro:  
  
    1.  Haga clic en **Inicio** y, a continuación, haga clic en **Ejecutar**.  
  
    2.  En el cuadro **Abrir**, escriba **regedt32.exe** y haga clic en **Aceptar**.  
  
2.  Busque la siguiente clave del Registro:  
  
     \\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel  
  
     Si la clave no existe, créela.  
  
3.  Agregue las subclaves siguientes como **Valor alfanumérico**, si no existen ya, junto con los valores asociados.  
  
    |Subclave de valor alfanumérico|Valor|  
    |------------------------------------|-----------|  
    |**Internet**|**AuthenticodeRequired**|  
    |**UntrustedSites**|**Disabled**|  
    |**MyComputer**|**Enabled**|  
    |**LocalIntranet**|**Enabled**|  
    |**TrustedSites**|**Enabled**|  
  
     De forma predeterminada, **Internet** tiene el valor **AuthenticodeRequired** y **UntrustedSites** tiene el valor **Disabled**.  
  
#### Para habilitar la lista de inclusión mediante programación  
  
1.  Cree una aplicación de consola de Visual Basic o Visual C\#.  
  
2.  Abra el archivo Program.vb o Program.cs para modificarlo y agregue el código siguiente.  
  
    ```vb  
    Dim key As Microsoft.Win32.RegistryKey  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")  
    key.SetValue("MyComputer", "Enabled")  
    key.SetValue("LocalIntranet", "Enabled")  
    key.SetValue("Internet", "AuthenticodeRequired")  
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
  
## Restringir la lista de inclusión  
 Restrinja la lista de inclusión para que las soluciones se deban firmar con certificados Authenticode que dispongan de una identidad conocida antes de que se pida a los usuarios una decisión relativa a la confianza.  
  
#### Para restringir la lista de inclusión  
  
1.  Abra el editor del Registro:  
  
    1.  Haga clic en **Inicio** y, a continuación, haga clic en **Ejecutar**.  
  
    2.  En el cuadro **Abrir**, escriba **regedt32.exe** y haga clic en **Aceptar**.  
  
2.  Busque la siguiente clave del Registro:  
  
     \\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel  
  
     Si la clave no existe, créela.  
  
3.  Agregue las subclaves siguientes como **Valor alfanumérico**, si no existen ya, junto con los valores asociados.  
  
    |Subclave de valor alfanumérico|Valor|  
    |------------------------------------|-----------|  
    |**UntrustedSites**|**Disabled**|  
    |**Internet**|**AuthenticodeRequired**|  
    |**MyComputer**|**AuthenticodeRequired**|  
    |**LocalIntranet**|**AuthenticodeRequired**|  
    |**TrustedSites**|**AuthenticodeRequired**|  
  
     De forma predeterminada, **Internet** tiene el valor **AuthenticodeRequired** y **UntrustedSites** tiene el valor **Disabled**.  
  
#### Para restringir la lista de inclusión mediante programación  
  
1.  Cree una aplicación de consola de Visual Basic o Visual C\#.  
  
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
  
## Deshabilitar la lista de inclusión  
 Puede deshabilitar la lista de inclusión para que los usuarios finales sólo puedan instalar soluciones firmadas con un certificado de confianza y conocido.  
  
#### Para deshabilitar la lista de inclusión  
  
1.  Abra el editor del Registro:  
  
    1.  Haga clic en **Inicio** y, a continuación, haga clic en **Ejecutar**.  
  
    2.  En el cuadro **Abrir**, escriba **regedt32.exe** y haga clic en **Aceptar**.  
  
2.  Cree la siguiente clave del Registro si aún no existe:  
  
     **\\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel**  
  
3.  Agregue las subclaves siguientes como **Valor alfanumérico**, si no existen ya, junto con los valores asociados.  
  
    |Subclave de valor alfanumérico|Valor|  
    |------------------------------------|-----------|  
    |**UntrustedSites**|**Disabled**|  
    |**Internet**|**Disabled**|  
    |**MyComputer**|**Disabled**|  
    |**LocalIntranet**|**Disabled**|  
    |**TrustedSites**|**Disabled**|  
  
#### Para deshabilitar la lista de inclusión mediante programación  
  
1.  Cree una aplicación de consola de Visual Basic o Visual C\#.  
  
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
  
## Vea también  
 [Otorgar confianza a las soluciones de Office mediante listas de inclusión](../vsto/trusting-office-solutions-by-using-inclusion-lists.md)   
 [Asegurar las soluciones de Office](../vsto/securing-office-solutions.md)  
  
  