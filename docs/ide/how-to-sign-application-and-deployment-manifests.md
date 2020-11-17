---
title: Procedimiento Firmar manifiestos de implementación y aplicación
description: Obtenga información sobre los requisitos de firma para la publicación de manifiestos de aplicación e implementación ClickOnce. La firma es opcional en el caso de las aplicaciones basadas en .exe.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
helpviewer_keywords:
- manifests [Visual Studio]
- code signing [Visual Studio], Authenticode
- deployment manifests [Visual Studio]
- signing manifests [Visual Studio]
- application manifests [Visual Studio]
- ClickOnce deployment [Visual Studio], signing assemblies
- key files [Visual Studio]
- assemblies [Visual Studio], signing
ms.assetid: 64173505-8bfb-41cf-a0de-b9075173f3a2
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a267a64a6b6d59b64ffb70596154d1e54f368410
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2020
ms.locfileid: "94351276"
---
# <a name="how-to-sign-application-and-deployment-manifests"></a>Cómo: Firmar aplicaciones y manifiestos de implementación

Si quiere publicar una aplicación mediante la implementación ClickOnce, los manifiestos de aplicación e implementación deben estar firmados con un par de claves pública y privada mediante la tecnología Authenticode. Puede firmar los manifiestos con un certificado del almacén de certificados de Windows o un archivo de clave.

Para obtener más información sobre la implementación ClickOnce, consulte [Seguridad e implementación ClickOnce](../deployment/clickonce-security-and-deployment.md).

Firmar los manifiestos de ClickOnce es opcional para aplicaciones basadas en *.exe*. Para obtener más información, consulte la sección "Generar manifiestos sin firmar" de este documento.

Para obtener información sobre la creación de archivos de claves, consulte [Cómo: Crear un par de claves privada y pública](/dotnet/framework/app-domains/how-to-create-a-public-private-key-pair).

> [!NOTE]
> Visual Studio solo admite archivos de claves de intercambio de información personal (PFX) que tienen la extensión *.pfx*. En cambio, puede seleccionar otros tipos de certificados desde el almacén de certificados de Windows del usuario actual si hace clic en **Seleccionar del almacén** en la página **Firma** de las propiedades del proyecto.

## <a name="sign-using-a-certificate"></a>Inicio de sesión con un certificado

1. Vaya a la ventana de propiedades del proyecto (haga clic con el botón derecho en el nodo del proyecto en el **Explorador de soluciones** y seleccione **Propiedades**). En la pestaña **Firma**, active la casilla **Firmar los manifiestos de ClickOnce**.

2. Haga clic en el botón **Seleccionar del almacén**.

     Aparece el cuadro de diálogo **Seleccionar un certificado** y se muestra el contenido del almacén de certificados de Windows.

    > [!TIP]
    > Si hace clic en **Haga clic aquí para ver las propiedades del certificado**, aparece el cuadro de diálogo **Detalles del certificado**. Este cuadro de diálogo incluye información detallada sobre el certificado y opciones adicionales. Haga clic en **Certificados** para ver información de ayuda adicional.

3. Seleccione el certificado que quiera usar para firmar los manifiestos.

4. Además, puede especificar la dirección de un servidor de marca de tiempo en el cuadro de texto **Dirección URL del servidor de marca de tiempo**. Se trata de un servidor que proporciona una marca de tiempo que especifica cuándo se ha firmado el manifiesto.

## <a name="sign-using-an-existing-key-file"></a>Inicio de sesión con un archivo de clave existente

1. En la página **Firma**, active la casilla **Firmar los manifiestos de ClickOnce**.

2. Haga clic en el botón **Seleccionar de archivo**.

     Aparece el cuadro de diálogo **Seleccionar archivo**.

3. En el cuadro de diálogo **Seleccionar archivo**, vaya a la ubicación del archivo de claves (*.pfx*) que quiere usar y después haga clic en **Abrir**.

    > [!NOTE]
    > Esta opción solo admite archivos que tengan la extensión *.pfx*. Si tiene un archivo de claves o un certificado en otro formato, almacénelo en el almacén de certificados de Windows y seleccione el certificado como se describe en el procedimiento anterior. El propósito del certificado seleccionado debe incluir firma de código.

     Aparece el cuadro de diálogo **Escribir la contraseña para abrir el archivo**. (Si el archivo *.pfx* ya está almacenado en el almacén de certificados de Windows o no está protegido por contraseña, no se le pedirá que escriba una contraseña).

4. Escriba la contraseña para acceder al archivo de claves y seleccione **ENTRAR**.

> [!NOTE]
> El archivo *.pfx* no puede incluir información de encadenamiento de certificados. Si lo hace, se producirá el siguiente error de importación: **No se encuentra el certificado y la clave privada para el descifrado**. Para quitar la información de encadenamiento de certificados, puede usar *Certmgr.msc* y [deshabilitar la opción](/previous-versions/aa730868(v=vs.80))**Incluir todos los certificados** al exportar el archivo *.pfx.

## <a name="sign-using-a-test-certificate"></a>Inicio de sesión con un certificado de prueba

1. En la página **Firma**, active la casilla **Firmar los manifiestos de ClickOnce**.

2. Para crear un certificado de prueba, haga clic en el botón **Crear certificado de prueba**.

3. En el cuadro de diálogo **Crear certificado de prueba**, escriba una contraseña para ayudar a proteger el certificado de prueba.

## <a name="generate-unsigned-manifests"></a>Generar manifiestos sin firmar

Firmar los manifiestos de ClickOnce es opcional para aplicaciones basadas en *.exe*. En los procedimientos siguientes, se muestra cómo generar manifiestos sin firmar de ClickOnce.

> [!IMPORTANT]
> Los manifiestos sin firmar pueden simplificar el desarrollo y las pruebas de la aplicación. En cambio, los manifiestos sin firmar introducen riesgos de seguridad considerables en un entorno de producción. Considere solo el uso de manifiestos sin firmar si la aplicación ClickOnce se ejecuta en equipos de una intranet que está completamente aislada de Internet u otros orígenes de código malintencionado.

De manera predeterminada, ClickOnce genera de forma automática manifiestos firmados a menos que se excluyan de forma específica uno o varios archivos del código hash generado. En otras palabras, si se incluyen todos los archivos en el código hash, la aplicación se publica con manifiestos firmados, incluso si la casilla **Firmar los manifiestos de ClickOnce** está desactivada.

### <a name="to-generate-unsigned-manifests-and-include-all-files-in-the-generated-hash"></a>Para generar manifiestos sin firmar e incluir todos los archivos en el código hash generado

1. Para generar manifiestos sin firmar que incluyan todos los archivos en el código hash, primero debe publicar la aplicación junto con los manifiestos firmados. Por tanto, firme primero los manifiestos de ClickOnce mediante uno de los procedimientos anteriores y después publique la aplicación.

2. En la página **Firma**, desactive la casilla **Firmar los manifiestos de ClickOnce**.

3. Restablezca la versión de publicación para que solo esté disponible una versión de la aplicación. De manera predeterminada, Visual Studio incrementa de forma automática el número de revisión de la versión de publicación cada vez que se publica una aplicación. Para obtener más información, consulte [Cómo: Establecer la versión de publicación de ClickOnce](../deployment/how-to-set-the-clickonce-publish-version.md).

4. Publique la aplicación.

### <a name="to-generate-unsigned-manifests-and-exclude-one-or-more-files-from-the-generated-hash"></a>Para generar manifiestos sin firmar y excluir uno o varios archivos del código hash generado

1. En la página **Firma**, desactive la casilla **Firmar los manifiestos de ClickOnce**.

2. Abra el cuadro de diálogo **Archivos de aplicación** y establezca **Hash** en **Excluir** para los archivos que quiera excluir del código hash generado.

    > [!NOTE]
    > Excluir un archivo del código hash configura ClickOnce para que deshabilite la firma automática de los manifiestos, por lo que no tiene que publicar primero con manifiestos firmados como se muestra en el procedimiento anterior.

3. Publique la aplicación.

## <a name="see-also"></a>Vea también

- [Ensamblados con nombre seguro](/dotnet/framework/app-domains/strong-named-assemblies)
- [Cómo: Crear un par de claves privada y pública](/dotnet/framework/app-domains/how-to-create-a-public-private-key-pair)
- [Página Firma, Diseñador de proyectos](../ide/reference/signing-page-project-designer.md)
- [Seguridad e implementación ClickOnce](../deployment/clickonce-security-and-deployment.md)
