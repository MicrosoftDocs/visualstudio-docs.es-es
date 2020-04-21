---
title: Procedimientos para configurar el comportamiento del mensaje relativo a la confianza de ClickOnce | Microsoft Docs
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ec5f1cca49f1b799b39969849e0a73bf1e6e296d
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649145"
---
# <a name="how-to-configure-the-clickonce-trust-prompt-behavior"></a>Procedimientos para configurar el comportamiento del mensaje relativo a la confianza de ClickOnce
Puede configurar el símbolo del sistema de confianza ClickOnce para controlar si los usuarios finales tienen la opción de instalar aplicaciones ClickOnce, como aplicaciones de Windows Forms, aplicaciones de Windows Presentation Foundation, aplicaciones de consola, aplicaciones de explorador WPF y soluciones de Office. Configure el símbolo del sistema de confianza estableciendo claves del Registro en el equipo de cada usuario final.

 En la tabla siguiente se muestran las opciones de configuración que se pueden aplicar a cada una de las cinco zonas (Internet, UntrustedSites, MyComputer, LocalIntranet y TrustedSites).

|Opción|Valor de configuración del registro|Descripción|
|------------|----------------------------|-----------------|
|Habilite el prompt de confianza.|`Enabled`|Se muestra el símbolo del sistema de confianza ClickOnce para que los usuarios finales puedan conceder confianza a las aplicaciones ClickOnce.|
|Restringir el mensaje de confianza.|`AuthenticodeRequired`|El símbolo del sistema de confianza ClickOnce solo se muestra si las aplicaciones ClickOnce están firmadas con un certificado que identifica al publicador.|
|Inhabilite el prompt de la confianza.|`Disabled`|El símbolo del sistema de confianza ClickOnce no se muestra para las aplicaciones ClickOnce que no están firmadas con un certificado de confianza explícita.|

 En la tabla siguiente se muestra el comportamiento predeterminado para cada zona. La columna Aplicaciones hace referencia a aplicaciones de Windows Forms, aplicaciones de Windows Presentation Foundation, aplicaciones de explorador WPF y aplicaciones de consola.

|Zona|APLICACIONES|soluciones de Office|
|----------|------------------|----------------------|
|`MyComputer`|`Enabled`|`Enabled`|
|`LocalIntranet`|`Enabled`|`Enabled`|
|`TrustedSites`|`Enabled`|`Enabled`|
|`Internet`|`Enabled`|`AuthenticodeRequired`|
|`UntrustedSites`|`Disabled`|`Disabled`|

 Puede invalidar esta configuración habilitando, restringiendo o deshabilitando el símbolo del sistema de confianza ClickOnce.

## <a name="enable-the-clickonce-trust-prompt"></a>Habilite el símbolo del sistema de confianza ClickOnce
 Habilite el símbolo del sistema de confianza para una zona cuando desee que los usuarios finales se presenten con la opción de instalar y ejecutar cualquier aplicación ClickOnce que provenga de esa zona.

#### <a name="to-enable-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Para habilitar el símbolo del sistema de confianza ClickOnce mediante el editor del Registro

1. Abra el Editor del Registro:

    1. Haga clic en **Inicio** y, a continuación, en **Ejecutar**.

    2. En **Open** el cuadro `regedit`Abrir , escriba y, a continuación, haga clic en **Aceptar**.

2. Busque la siguiente clave del Registro:

     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\.NETFramework\Security\TrustManager\PromptingLevel**

     Si la clave no existe, créela.

3. Agregue las siguientes subclaves como Valor de **cadena**, si aún no existen, con los valores asociados que se muestran en la tabla siguiente.

    |Subclave de valor de cadena|Valor|
    |-------------------------|-----------|
    |`Internet`|`Enabled`|
    |`UntrustedSites`|`Disabled`|
    |`MyComputer`|`Enabled`|
    |`LocalIntranet`|`Enabled`|
    |`TrustedSites`|`Enabled`|

     Para las `Internet` soluciones de `AuthenticodeRequired` Office, tiene el valor predeterminado y `UntrustedSites` tiene el valor `Disabled`. Para todos `Internet` los demás, tiene el valor `Enabled`predeterminado .

#### <a name="to-enable-the-clickonce-trust-prompt-programmatically"></a>Para habilitar el símbolo del sistema clickOnce trust mediante programación

1. Cree una aplicación de consola de Visual Basic o Visual C. en Visual Studio.

2. Abra el archivo *Program.vb* o *Program.cs* para editarlo y agregue el código siguiente.

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

3. Compile y ejecute la aplicación.

## <a name="restrict-the-clickonce-trust-prompt"></a>Restringir el símbolo del sistema de confianza ClickOnce
 Restringir el mensaje de confianza para que las soluciones se deben firmar con certificados Authenticode que tienen identidad conocida antes de que se solicite a los usuarios una decisión de confianza.

#### <a name="to-restrict-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Para restringir el mensaje de confianza ClickOnce mediante el editor del Registro

1. Abra el Editor del Registro:

    1. Haga clic en **Inicio** y, a continuación, en **Ejecutar**.

    2. En **Open** el cuadro `regedit`Abrir , escriba y, a continuación, haga clic en **Aceptar**.

2. Busque la siguiente clave del Registro:

     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\.NETFramework\Security\TrustManager\PromptingLevel**

     Si la clave no existe, créela.

3. Agregue las siguientes subclaves como Valor de **cadena**, si aún no existen, con los valores asociados que se muestran en la tabla siguiente.

    |Subclave de valor de cadena|Valor|
    |-------------------------|-----------|
    |`UntrustedSites`|`Disabled`|
    |`Internet`|`AuthenticodeRequired`|
    |`MyComputer`|`AuthenticodeRequired`|
    |`LocalIntranet`|`AuthenticodeRequired`|
    |`TrustedSites`|`AuthenticodeRequired`|

#### <a name="to-restrict-the-clickonce-trust-prompt-programmatically"></a>Para restringir el símbolo del sistema clickOnce trust mediante programación

1. Cree una aplicación de consola de Visual Basic o Visual C. en Visual Studio.

2. Abra el archivo *Program.vb* o *Program.cs* para editarlo y agregue el código siguiente.

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

## <a name="disable-the-clickonce-trust-prompt"></a>Deshabilite el símbolo del sistema de confianza ClickOnce
 Puede deshabilitar el símbolo del sistema de confianza para que los usuarios finales no tenga la opción de instalar soluciones que aún no son de confianza en su directiva de seguridad.

#### <a name="to-disable-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Para deshabilitar el símbolo del sistema de confianza ClickOnce mediante el editor del Registro

1. Abra el Editor del Registro:

    1. Haga clic en **Inicio** y, a continuación, en **Ejecutar**.

    2. En **Open** el cuadro `regedit`Abrir , escriba y, a continuación, haga clic en **Aceptar**.

2. Busque la siguiente clave del Registro:

     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\.NETFramework\Security\TrustManager\PromptingLevel**

     Si la clave no existe, créela.

3. Agregue las siguientes subclaves como Valor de **cadena**, si aún no existen, con los valores asociados que se muestran en la tabla siguiente.

    |Subclave de valor de cadena|Valor|
    |-------------------------|-----------|
    |`UntrustedSites`|`Disabled`|
    |`Internet`|`Disabled`|
    |`MyComputer`|`Disabled`|
    |`LocalIntranet`|`Disabled`|
    |`TrustedSites`|`Disabled`|

#### <a name="to-disable-the-clickonce-trust-prompt-programmatically"></a>Para deshabilitar el símbolo del sistema clickOnce trust mediante programación

1. Cree una aplicación de consola de Visual Basic o Visual C. en Visual Studio.

2. Abra el archivo *Program.vb* o *Program.cs* para editarlo y agregue el código siguiente.

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
- [Protección de las aplicaciones ClickOnce](../deployment/securing-clickonce-applications.md)
- [Seguridad de acceso del código para aplicaciones ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)
- [ClickOnce y Authenticode](../deployment/clickonce-and-authenticode.md)
- [Introducción a la implementación de aplicaciones de confianza](../deployment/trusted-application-deployment-overview.md)
- [Procedimientos para habilitar la configuración de seguridad de ClickOnce](../deployment/how-to-enable-clickonce-security-settings.md)
- [Procedimientos para establecer una zona de seguridad para una aplicación ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)
- [Procedimientos para establecer permisos personalizados para una aplicación ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)
- [Procedimientos para depurar una aplicación ClickOnce con permisos restringidos](securing-clickonce-applications.md)
- [Procedimientos para agregar un publicador de confianza a un equipo cliente para aplicaciones ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)
- [Procedimientos para volver a firmar manifiestos de aplicación e implementación](../deployment/how-to-re-sign-application-and-deployment-manifests.md)
