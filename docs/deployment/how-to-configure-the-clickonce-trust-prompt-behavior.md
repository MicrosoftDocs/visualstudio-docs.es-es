---
title: Cómo configurar el comportamiento del mensaje de confianza de ClickOnce | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: 7417f9cdce21dc09aeaf306b55834ad7d3a125a6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85382554"
---
# <a name="how-to-configure-the-clickonce-trust-prompt-behavior"></a>Procedimientos para configurar el comportamiento del mensaje relativo a la confianza de ClickOnce
Puede configurar el aviso de confianza de ClickOnce para controlar si los usuarios finales tienen la opción de instalar aplicaciones ClickOnce, como Windows Forms aplicaciones, Windows Presentation Foundation aplicaciones, aplicaciones de consola, aplicaciones de explorador WPF y soluciones de Office. Configure el mensaje de confianza mediante la configuración de las claves del registro en el equipo de cada usuario final.

 En la tabla siguiente se muestran las opciones de configuración que se pueden aplicar a cada una de las cinco zonas (Internet, UntrustedSites, equipo, LocalIntranet y TrustedSites).

|Opción|Valor de configuración del registro|Descripción|
|------------|----------------------------|-----------------|
|Habilite el aviso de confianza.|`Enabled`|Se muestra el mensaje de confianza de ClickOnce para que los usuarios finales puedan conceder confianza a las aplicaciones ClickOnce.|
|Restrinja el aviso de confianza.|`AuthenticodeRequired`|El aviso de confianza de ClickOnce solo se muestra si las aplicaciones ClickOnce están firmadas con un certificado que identifica al publicador.|
|Deshabilite el aviso de confianza.|`Disabled`|El aviso de confianza de ClickOnce no se muestra para las aplicaciones ClickOnce que no estén firmadas con un certificado de confianza explícita.|

 En la tabla siguiente se muestra el comportamiento predeterminado de cada zona. La columna aplicaciones hace referencia a Windows Forms aplicaciones, Windows Presentation Foundation aplicaciones, aplicaciones de explorador WPF y aplicaciones de consola.

|Zona|APLICACIONES|soluciones de Office|
|----------|------------------|----------------------|
|`MyComputer`|`Enabled`|`Enabled`|
|`LocalIntranet`|`Enabled`|`Enabled`|
|`TrustedSites`|`Enabled`|`Enabled`|
|`Internet`|`Enabled`|`AuthenticodeRequired`|
|`UntrustedSites`|`Disabled`|`Disabled`|

 Puede invalidar esta configuración habilitando, restringiendo o deshabilitando el aviso de confianza de ClickOnce.

## <a name="enable-the-clickonce-trust-prompt"></a>Habilitar el mensaje de confianza de ClickOnce
 Habilite el aviso de confianza para una zona cuando desee que se presente a los usuarios finales la opción de instalar y ejecutar cualquier aplicación ClickOnce que proceda de esa zona.

#### <a name="to-enable-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Para habilitar el aviso de confianza de ClickOnce mediante el editor del registro

1. Abra el Editor del Registro:

    1. Haga clic en **Inicio**y, a continuación, haga clic en **Ejecutar**.

    2. En el cuadro **abrir** , escriba `regedit` y, a continuación, haga clic en **Aceptar**.

2. Busque la siguiente clave del registro:

     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\.NETFramework\Security\TrustManager\PromptingLevel**

     Si la clave no existe, créela.

3. Agregue las siguientes subclaves como **valor de cadena**, si aún no existen, con los valores asociados que se muestran en la tabla siguiente.

    |Subclave de valor de cadena|Value|
    |-------------------------|-----------|
    |`Internet`|`Enabled`|
    |`UntrustedSites`|`Disabled`|
    |`MyComputer`|`Enabled`|
    |`LocalIntranet`|`Enabled`|
    |`TrustedSites`|`Enabled`|

     En el caso de las soluciones de Office, `Internet` tiene el valor predeterminado `AuthenticodeRequired` y `UntrustedSites` tiene el valor `Disabled` . Para todos los demás, `Internet` tiene el valor predeterminado `Enabled` .

#### <a name="to-enable-the-clickonce-trust-prompt-programmatically"></a>Para habilitar el aviso de confianza de ClickOnce mediante programación

1. Cree una aplicación de consola de Visual Basic o Visual C# en Visual Studio.

2. Abra el archivo *Program. VB* o *Program.CS* para editarlo y agregue el código siguiente.

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

## <a name="restrict-the-clickonce-trust-prompt"></a>Restringir el aviso de confianza de ClickOnce
 Restrinja el aviso de confianza para que las soluciones se deban firmar con certificados Authenticode que tengan una identidad conocida antes de que se pida a los usuarios una decisión de confianza.

#### <a name="to-restrict-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Para restringir el aviso de confianza de ClickOnce mediante el editor del registro

1. Abra el Editor del Registro:

    1. Haga clic en **Inicio**y, a continuación, haga clic en **Ejecutar**.

    2. En el cuadro **abrir** , escriba `regedit` y, a continuación, haga clic en **Aceptar**.

2. Busque la siguiente clave del registro:

     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\.NETFramework\Security\TrustManager\PromptingLevel**

     Si la clave no existe, créela.

3. Agregue las siguientes subclaves como **valor de cadena**, si aún no existen, con los valores asociados que se muestran en la tabla siguiente.

    |Subclave de valor de cadena|Value|
    |-------------------------|-----------|
    |`UntrustedSites`|`Disabled`|
    |`Internet`|`AuthenticodeRequired`|
    |`MyComputer`|`AuthenticodeRequired`|
    |`LocalIntranet`|`AuthenticodeRequired`|
    |`TrustedSites`|`AuthenticodeRequired`|

#### <a name="to-restrict-the-clickonce-trust-prompt-programmatically"></a>Para restringir el aviso de confianza de ClickOnce mediante programación

1. Cree una aplicación de consola de Visual Basic o Visual C# en Visual Studio.

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

## <a name="disable-the-clickonce-trust-prompt"></a>Deshabilitar el mensaje de confianza de ClickOnce
 Puede deshabilitar el aviso de confianza para que a los usuarios finales no se les proporcione la opción de instalar soluciones que no sean de confianza en su Directiva de seguridad.

#### <a name="to-disable-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Para deshabilitar el mensaje de confianza de ClickOnce mediante el editor del registro

1. Abra el Editor del Registro:

    1. Haga clic en **Inicio**y, a continuación, haga clic en **Ejecutar**.

    2. En el cuadro **abrir** , escriba `regedit` y, a continuación, haga clic en **Aceptar**.

2. Busque la siguiente clave del registro:

     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\.NETFramework\Security\TrustManager\PromptingLevel**

     Si la clave no existe, créela.

3. Agregue las siguientes subclaves como **valor de cadena**, si aún no existen, con los valores asociados que se muestran en la tabla siguiente.

    |Subclave de valor de cadena|Value|
    |-------------------------|-----------|
    |`UntrustedSites`|`Disabled`|
    |`Internet`|`Disabled`|
    |`MyComputer`|`Disabled`|
    |`LocalIntranet`|`Disabled`|
    |`TrustedSites`|`Disabled`|

#### <a name="to-disable-the-clickonce-trust-prompt-programmatically"></a>Para deshabilitar el mensaje de confianza de ClickOnce mediante programación

1. Cree una aplicación de consola de Visual Basic o Visual C# en Visual Studio.

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

## <a name="see-also"></a>Vea también
- [Protección de las aplicaciones ClickOnce](../deployment/securing-clickonce-applications.md)
- [Seguridad de acceso del código para aplicaciones ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)
- [ClickOnce y Authenticode](../deployment/clickonce-and-authenticode.md)
- [Introducción a la implementación de aplicaciones de confianza](../deployment/trusted-application-deployment-overview.md)
- [Cómo: habilitar la configuración de seguridad de ClickOnce](../deployment/how-to-enable-clickonce-security-settings.md)
- [Cómo: establecer una zona de seguridad para una aplicación ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)
- [Cómo: establecer permisos personalizados para una aplicación ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)
- [Procedimientos para depurar una aplicación ClickOnce con permisos restringidos](securing-clickonce-applications.md)
- [Procedimientos para agregar un publicador de confianza a un equipo cliente para aplicaciones ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)
- [Procedimientos para volver a firmar manifiestos de aplicación e implementación](../deployment/how-to-re-sign-application-and-deployment-manifests.md)
