---
title: Procedimiento Configurar la seguridad de la lista de inclusión
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- permissions [Office development in Visual Studio
- inclusion lists [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: b13084a0010bef21283dc7890dd5b1064392e1b2
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2018
ms.locfileid: "53647740"
---
# <a name="how-to-configure-inclusion-list-security"></a>Procedimiento Configurar la seguridad de la lista de inclusión
  Si tiene permisos de administrador, puede configurar el [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] confiar símbolo del sistema para controlar si los usuarios finales tienen la opción de instalar soluciones de Office al guardar una decisión de confianza en la lista de inclusión. Para obtener información acerca de las listas de inclusión, vea [soluciones de Office de confianza mediante el uso de las listas de inclusión](../vsto/trusting-office-solutions-by-using-inclusion-lists.md).  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Para las soluciones que se encuentran en cada uno de los cinco zonas, puede establecer las siguientes opciones:  
  
-   Habilitar la [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] confiar la clave del mensaje y la lista de inclusión. Puede permitir que los usuarios finales conceder confianza a las soluciones de Office que se firman con cualquier certificado.  
  
-   Restringir el [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] confiar la clave del mensaje y la lista de inclusión. Puede permitir que los usuarios finales instalar soluciones de Office que estén firmadas con un certificado que identifica el publicador, pero que no es de confianza.  
  
-   Deshabilitar el [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] confiar la clave del mensaje y la lista de inclusión. Puede impedir que los usuarios finales instalar cualquier solución de Office que no está firmado con un certificado de confianza explícita.  
  
## <a name="enable-the-inclusion-list"></a>Habilitar la lista de inclusión  
 Habilitar la lista de inclusión de una zona cuando desee que los usuarios finales se le ofrecerá la opción de instalar y ejecutar cualquier solución de Office que procede de esa zona.  
  
### <a name="to-enable-the-inclusion-list-by-using-the-registry-editor"></a>Para habilitar la lista de inclusión con el editor del registro  
  
1.  Abra el editor del registro:  
  
    1.  Haga clic en **iniciar**y, a continuación, haga clic en **ejecutar**.  
  
    2.  En el **abierto** , escriba **regedt32.exe**y, a continuación, haga clic en **Aceptar**.  
  
2.  Busque la siguiente clave del registro:  
  
     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\. NETFramework\Security\TrustManager\PromptingLevel**  
  
     Si la clave no existe, créelo.  
  
3.  Agregue las siguientes subclaves como **valor de cadena**, si no existe ya, con los valores asociados.  
  
    |Subclave de valor de cadena|Valor|  
    |-------------------------|-----------|  
    |**Internet**|**AuthenticodeRequired**|  
    |**UntrustedSites**|**Deshabilitado**|  
    |**Mi PC**|**Habilitado**|  
    |**Intranet local**|**Habilitado**|  
    |**TrustedSites**|**Habilitado**|  
  
     De forma predeterminada, **Internet** tiene el valor **AuthenticodeRequired** y **UntrustedSites** tiene el valor **deshabilitado**.  
  
### <a name="to-enable-the-inclusion-list-programmatically"></a>Para habilitar la lista de inclusión mediante programación  
  
1.  Cree una aplicación de consola de Visual Basic o Visual C#.  
  
2.  Abra el *Program.vb* o *Program.cs* para editarlo y agréguele el código siguiente.  
  
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
  
## <a name="restrict-the-inclusion-list"></a>Restringir la lista de inclusión  
 Restringir la lista de inclusión para que las soluciones deben estar firmadas con certificados de Authenticode que dispongan de una identidad conocida antes de que los usuarios se le solicitará una decisión de confianza.  
  
### <a name="to-restrict-the-inclusion-list"></a>Para restringir la lista de inclusión  
  
1.  Abra el editor del registro:  
  
    1.  Haga clic en **iniciar**y, a continuación, haga clic en **ejecutar**.  
  
    2.  En el **abierto** , escriba **regedt32.exe**y, a continuación, haga clic en **Aceptar**.  
  
2.  Busque la siguiente clave del registro:  
  
     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\. NETFramework\Security\TrustManager\PromptingLevel**  
  
     Si la clave no existe, créelo.  
  
3.  Agregue las siguientes subclaves como **valor de cadena**, si no existe ya, con los valores asociados.  
  
    |Subclave de valor de cadena|Valor|  
    |-------------------------|-----------|  
    |**UntrustedSites**|**Deshabilitado**|  
    |**Internet**|**AuthenticodeRequired**|  
    |**Mi PC**|**AuthenticodeRequired**|  
    |**Intranet local**|**AuthenticodeRequired**|  
    |**TrustedSites**|**AuthenticodeRequired**|  
  
     De forma predeterminada, **Internet** tiene el valor **AuthenticodeRequired** y **UntrustedSites** tiene el valor **deshabilitado**.  
  
### <a name="to-restrict-the-inclusion-list-programmatically"></a>Para restringir la lista de inclusión mediante programación  
  
1.  Cree una aplicación de consola de Visual Basic o Visual C#.  
  
2.  Abra el *Program.vb* o *Program.cs* para editarlo y agréguele el código siguiente.  
  
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
  
## <a name="disable-the-inclusion-list"></a>Deshabilitar la lista de inclusión  
 Puede deshabilitar la lista de inclusión para que los usuarios finales solo puede instalar las soluciones que estén firmadas con un certificado conocido y de confianza.  
  
### <a name="to-disable-the-inclusion-list"></a>Para deshabilitar la lista de inclusión  
  
1.  Abra el editor del registro:  
  
    1.  Haga clic en **iniciar**y, a continuación, haga clic en **ejecutar**.  
  
    2.  En el **abierto** , escriba **regedt32.exe**y, a continuación, haga clic en **Aceptar**.  
  
2.  Si esto no existe, cree la siguiente clave del registro:  
  
     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\. NETFramework\Security\TrustManager\PromptingLevel**  
  
3.  Agregue las siguientes subclaves como **valor de cadena**, si no existe ya, con los valores asociados.  
  
    |Subclave de valor de cadena|Valor|  
    |-------------------------|-----------|  
    |**UntrustedSites**|**Deshabilitado**|  
    |**Internet**|**Deshabilitado**|  
    |**Mi PC**|**Deshabilitado**|  
    |**Intranet local**|**Deshabilitado**|  
    |**TrustedSites**|**Deshabilitado**|  
  
### <a name="to-disable-the-inclusion-list-programmatically"></a>Para deshabilitar la lista de inclusión mediante programación  
  
1.  Cree una aplicación de consola de Visual Basic o Visual C#.  
  
2.  Abra el *Program.vb* o *Program.cs* para editarlo y agréguele el código siguiente.  
  
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
 [Confiar en soluciones de Office mediante listas de inclusión](../vsto/trusting-office-solutions-by-using-inclusion-lists.md)   
 [Proteger soluciones de Office](../vsto/securing-office-solutions.md)  
  
  