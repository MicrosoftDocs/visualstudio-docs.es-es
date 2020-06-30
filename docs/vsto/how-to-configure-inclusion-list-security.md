---
title: 'Cómo: configurar la seguridad de la lista de inclusión'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- permissions [Office development in Visual Studio
- inclusion lists [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 459cf3f33197939a916a5f11a94bbaf09e8142e3
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85541640"
---
# <a name="how-to-configure-inclusion-list-security"></a>Cómo: configurar la seguridad de la lista de inclusión
  Si tiene permisos de administrador, puede configurar el [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] aviso de confianza para controlar si los usuarios finales tienen la opción de instalar soluciones de Office guardando una decisión de confianza en la lista de inclusión. Para obtener información sobre las listas de inclusión, consulte [confiar en las soluciones de Office mediante listas de inclusión](../vsto/trusting-office-solutions-by-using-inclusion-lists.md).

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 En el caso de las soluciones que se encuentran en cada una de las cinco zonas, puede establecer las siguientes opciones:

- Habilitar la [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] clave de mensaje de confianza y la lista de inclusión. Puede permitir a los usuarios finales conceder confianza a las soluciones de Office firmadas con cualquier certificado.

- Restrinja la [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] clave de mensajes de confianza y la lista de inclusión. Puede permitir que los usuarios finales instalen soluciones de Office firmadas con un certificado que identifique al publicador, pero que aún no son de confianza.

- Deshabilite la [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] clave de mensajes de confianza y la lista de inclusión. Puede impedir que los usuarios finales instalen cualquier solución de Office que no esté firmada con un certificado de confianza explícita.

## <a name="enable-the-inclusion-list"></a>Habilitar la lista de inclusión
 Habilite la lista de inclusión de una zona cuando quiera que se presenten los usuarios finales con la opción de instalar y ejecutar cualquier solución de Office que proceda de esa zona.

### <a name="to-enable-the-inclusion-list-by-using-the-registry-editor"></a>Para habilitar la lista de inclusión mediante el editor del registro

1. Abra el Editor del Registro:

    1. Haga clic en **Inicio**y, a continuación, haga clic en **Ejecutar**.

    2. En el cuadro **abrir** , escriba **regedt32.exe**y, a continuación, haga clic en **Aceptar**.

2. Busque la siguiente clave del registro:

     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\.NETFramework\Security\TrustManager\PromptingLevel**

     Si la clave no existe, créela.

3. Agregue las siguientes subclaves como **valor de cadena**, si aún no existen, con los valores asociados.

    |Subclave de valor de cadena|Value|
    |-------------------------|-----------|
    |**Internet**|**AuthenticodeRequired**|
    |**UntrustedSites**|**Deshabilitada**|
    |**MyComputer**|**Enabled**|
    |**LocalIntranet**|**Enabled**|
    |**TrustedSites**|**Enabled**|

     De forma predeterminada, **Internet** tiene el valor **AuthenticodeRequired** y **UntrustedSites** tiene el valor **Disabled**.

### <a name="to-enable-the-inclusion-list-programmatically"></a>Para habilitar la lista de inclusión mediante programación

1. Cree una aplicación de consola de Visual Basic o Visual C#.

2. Abra el archivo *Program. VB* o *Program.CS* para editarlo y agregue el código siguiente.

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

3. Compile y ejecute la aplicación.

## <a name="restrict-the-inclusion-list"></a>Restringir la lista de inclusión
 Restrinja la lista de inclusión para que las soluciones se deban firmar con certificados Authenticode que tengan una identidad conocida antes de que se pida a los usuarios una decisión de confianza.

### <a name="to-restrict-the-inclusion-list"></a>Para restringir la lista de inclusión

1. Abra el Editor del Registro:

    1. Haga clic en **Inicio**y, a continuación, haga clic en **Ejecutar**.

    2. En el cuadro **abrir** , escriba **regedt32.exe**y, a continuación, haga clic en **Aceptar**.

2. Busque la siguiente clave del registro:

     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\.NETFramework\Security\TrustManager\PromptingLevel**

     Si la clave no existe, créela.

3. Agregue las siguientes subclaves como **valor de cadena**, si aún no existen, con los valores asociados.

    |Subclave de valor de cadena|Value|
    |-------------------------|-----------|
    |**UntrustedSites**|**Deshabilitada**|
    |**Internet**|**AuthenticodeRequired**|
    |**MyComputer**|**AuthenticodeRequired**|
    |**LocalIntranet**|**AuthenticodeRequired**|
    |**TrustedSites**|**AuthenticodeRequired**|

     De forma predeterminada, **Internet** tiene el valor **AuthenticodeRequired** y **UntrustedSites** tiene el valor **Disabled**.

### <a name="to-restrict-the-inclusion-list-programmatically"></a>Para restringir la lista de inclusión mediante programación

1. Cree una aplicación de consola de Visual Basic o Visual C#.

2. Abra el archivo *Program. VB* o *Program.CS* para editarlo y agregue el código siguiente.

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

3. Compile y ejecute la aplicación.

## <a name="disable-the-inclusion-list"></a>Deshabilitar la lista de inclusión
 Puede deshabilitar la lista de inclusión para que los usuarios finales solo puedan instalar soluciones que estén firmadas con un certificado conocido y de confianza.

### <a name="to-disable-the-inclusion-list"></a>Para deshabilitar la lista de inclusión

1. Abra el Editor del Registro:

    1. Haga clic en **Inicio**y, a continuación, haga clic en **Ejecutar**.

    2. En el cuadro **abrir** , escriba **regedt32.exe**y, a continuación, haga clic en **Aceptar**.

2. Cree la siguiente clave del registro si aún no existe:

     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\.NETFramework\Security\TrustManager\PromptingLevel**

3. Agregue las siguientes subclaves como **valor de cadena**, si aún no existen, con los valores asociados.

    |Subclave de valor de cadena|Value|
    |-------------------------|-----------|
    |**UntrustedSites**|**Deshabilitada**|
    |**Internet**|**Deshabilitada**|
    |**MyComputer**|**Deshabilitada**|
    |**LocalIntranet**|**Deshabilitada**|
    |**TrustedSites**|**Deshabilitada**|

### <a name="to-disable-the-inclusion-list-programmatically"></a>Para deshabilitar la lista de inclusión mediante programación

1. Cree una aplicación de consola de Visual Basic o Visual C#.

2. Abra el archivo *Program. VB* o *Program.CS* para editarlo y agregue el código siguiente.

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

3. Compile y ejecute la aplicación.

## <a name="see-also"></a>Consulte también
- [Confiar en soluciones de Office mediante listas de inclusión](../vsto/trusting-office-solutions-by-using-inclusion-lists.md)
- [Proteger soluciones de Office](../vsto/securing-office-solutions.md)
