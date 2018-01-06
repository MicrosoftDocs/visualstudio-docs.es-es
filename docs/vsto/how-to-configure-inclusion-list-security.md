---
title: "Cómo: configurar la seguridad de la lista de inclusión | Documentos de Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- permissions [Office development in Visual Studio
- inclusion lists [Office development in Visual Studio]
ms.assetid: 0609d8f0-4630-4e17-aeb3-14f3134165cf
caps.latest.revision: "26"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 09ea283b17a980ff9be1fae54ecc8b24912b70ad
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-configure-inclusion-list-security"></a>Cómo: Configurar la seguridad de la lista de inclusión
  Si tiene permisos de administrador, puede configurar el [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] confianza símbolo del sistema para controlar si los usuarios finales tienen la opción de instalar soluciones de Office y guarda una decisión de confianza en la lista de inclusión. Para obtener información acerca de las listas de inclusión, vea [confiar en soluciones de Office mediante listas de inclusión](../vsto/trusting-office-solutions-by-using-inclusion-lists.md).  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Para las soluciones que se encuentran en cada uno de los cinco zonas, puede establecer las siguientes opciones:  
  
-   Habilitar la [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] confiar en la clave del mensaje y la lista de inclusión. Puede permitir que los usuarios finales conceder confianza a las soluciones de Office que están firmados con un certificado.  
  
-   Restringir la [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] confiar en la clave del mensaje y la lista de inclusión. Puede permitir que los usuarios finales instalen las soluciones de Office que están firmadas con un certificado que identifica el publicador, pero que no es de confianza.  
  
-   Deshabilitar la [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] confiar en la clave del mensaje y la lista de inclusión. Puede impedir que los usuarios finales instalar cualquier solución de Office que no está firmado con un certificado de confianza explícita.  
  
## <a name="enabling-the-inclusion-list"></a>Habilitación de la lista de inclusión  
 Habilitar la lista de inclusión de una zona cuando desee que los usuarios finales se mostrará la opción de instalar y ejecutar cualquier solución de Office que procede de esa zona.  
  
#### <a name="to-enable-the-inclusion-list-by-using-the-registry-editor"></a>Para habilitar la lista de inclusión mediante el editor del registro  
  
1.  Abra el editor del registro:  
  
    1.  Haga clic en **iniciar**y, a continuación, haga clic en **ejecutar**.  
  
    2.  En el **abiertos** , escriba **regedt32.exe**y, a continuación, haga clic en **Aceptar**.  
  
2.  Busque la siguiente clave del registro:  
  
     \HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\. NETFramework\Security\TrustManager\PromptingLevel  
  
     Si la clave no existe, créela.  
  
3.  Agregue las subclaves siguientes como **valor de cadena**, si no existe ya, con los valores asociados.  
  
    |Subclave del valor de cadena|Valor|  
    |-------------------------|-----------|  
    |**Internet**|**AuthenticodeRequired**|  
    |**UntrustedSites**|**Deshabilitado**|  
    |**Mi PC**|**Habilitado**|  
    |**Intranet local**|**Habilitado**|  
    |**TrustedSites**|**Habilitado**|  
  
     De forma predeterminada, **Internet** tiene el valor **AuthenticodeRequired** y **UntrustedSites** tiene el valor **deshabilitado**.  
  
#### <a name="to-enable-the-inclusion-list-programmatically"></a>Para habilitar la lista de inclusión mediante programación  
  
1.  Cree una aplicación de consola de Visual Basic o Visual C#.  
  
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
  
## <a name="restricting-the-inclusion-list"></a>Restringir la lista de inclusión  
 Restringir la lista de inclusión de modo que las soluciones se deben firmar con certificados Authenticode que dispongan de una identidad conocida antes de que se piden a los usuarios una decisión de confianza.  
  
#### <a name="to-restrict-the-inclusion-list"></a>Para restringir la lista de inclusión  
  
1.  Abra el editor del registro:  
  
    1.  Haga clic en **iniciar**y, a continuación, haga clic en **ejecutar**.  
  
    2.  En el **abiertos** , escriba **regedt32.exe**y, a continuación, haga clic en **Aceptar**.  
  
2.  Busque la siguiente clave del registro:  
  
     \HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\. NETFramework\Security\TrustManager\PromptingLevel  
  
     Si la clave no existe, créela.  
  
3.  Agregue las subclaves siguientes como **valor de cadena**, si no existe ya, con los valores asociados.  
  
    |Subclave del valor de cadena|Valor|  
    |-------------------------|-----------|  
    |**UntrustedSites**|**Deshabilitado**|  
    |**Internet**|**AuthenticodeRequired**|  
    |**Mi PC**|**AuthenticodeRequired**|  
    |**Intranet local**|**AuthenticodeRequired**|  
    |**TrustedSites**|**AuthenticodeRequired**|  
  
     De forma predeterminada, **Internet** tiene el valor **AuthenticodeRequired** y **UntrustedSites** tiene el valor **deshabilitado**.  
  
#### <a name="to-restrict-the-inclusion-list-programmatically"></a>Para restringir la lista de inclusión mediante programación  
  
1.  Cree una aplicación de consola de Visual Basic o Visual C#.  
  
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
  
## <a name="disabling-the-inclusion-list"></a>Deshabilitación de la lista de inclusión  
 Puede deshabilitar la lista de inclusión para que los usuarios finales sólo puedan instalar soluciones que están firmadas con un certificado conocido y de confianza.  
  
#### <a name="to-disable-the-inclusion-list"></a>Para deshabilitar la lista de inclusión  
  
1.  Abra el editor del registro:  
  
    1.  Haga clic en **iniciar**y, a continuación, haga clic en **ejecutar**.  
  
    2.  En el **abiertos** , escriba **regedt32.exe**y, a continuación, haga clic en **Aceptar**.  
  
2.  Si esto no existe, cree la siguiente clave del registro:  
  
     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\. NETFramework\Security\TrustManager\PromptingLevel**  
  
3.  Agregue las subclaves siguientes como **valor de cadena**, si no existe ya, con los valores asociados.  
  
    |Subclave del valor de cadena|Valor|  
    |-------------------------|-----------|  
    |**UntrustedSites**|**Deshabilitado**|  
    |**Internet**|**Deshabilitado**|  
    |**Mi PC**|**Deshabilitado**|  
    |**Intranet local**|**Deshabilitado**|  
    |**TrustedSites**|**Deshabilitado**|  
  
#### <a name="to-disable-the-inclusion-list-programmatically"></a>Para deshabilitar la lista de inclusión mediante programación  
  
1.  Cree una aplicación de consola de Visual Basic o Visual C#.  
  
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
 [Otorgar confianza a las soluciones de Office mediante listas de inclusión](../vsto/trusting-office-solutions-by-using-inclusion-lists.md)   
 [Protección de soluciones de Office](../vsto/securing-office-solutions.md)  
  
  