---
title: Página Firma, Diseñador de proyectos | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.AddNewStrongNameKey
- ResolveKeySource.KeyFileForSignAssemblyNotImported
- vb.ProjectPropertiesSigning.ChangePasswordDialog
- ResolveKeySource.KeyFileForManifestNotImported
- vb.ProjectPropertiesSigning
- vb.ProjectPropertiesSigning.PasswordNeededDialog
- vb.ProjectPropertiesSigning.PfxPasswordDialog
helpviewer_keywords:
- Project Designer, Signing page
- Signing page in Project Designer
ms.assetid: dab3ba13-2f92-4827-92bd-1be3c35bc48b
caps.latest.revision: 39
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5707ef277892c37cab16f78ac11113194a95e190
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663510"
---
# <a name="signing-page-project-designer"></a>Página Firma, Diseñador de proyectos
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Use la página **Firma** del **Diseñador de proyectos** para firmar los manifiestos de aplicación e implementación y también para firmar el ensamblado (firma con nombre seguro).

 Tenga en cuenta que la firma de manifiestos de aplicación e implementación es un proceso distinto al de la firma de un ensamblado, aunque ambas tareas se realicen en la página **Firma**.

 Además, el almacenamiento de información de archivo de clave es diferente para la firma de manifiestos y la firma de ensamblados. En la firma de manifiestos, la información de clave se almacena en la base de datos de almacenamiento criptográfico del equipo y el almacén de certificados de Windows del usuario actual. En la firma de ensamblados, la información de clave se almacena únicamente en la base de datos de almacenamiento criptográfico del equipo.

 Para acceder a la página **Firma**, seleccione un nodo de proyecto en el **Explorador de soluciones** y, después, en el menú **Proyecto**, haga clic en **Propiedades**. Cuando se muestre el **Diseñador de proyectos**, haga clic en la pestaña **Firma**.

## <a name="application-and-deployment-manifest-signing"></a>Firma de manifiestos de aplicación e implementación
 Casilla **firmar los manifiestos de ClickOnce** Active esta casilla para firmar los manifiestos de implementación y aplicación con un par de claves pública y privada. Para obtener más información sobre cómo hacerlo, vea [Cómo: Firmar aplicaciones y manifiestos de implementación](../../ide/how-to-sign-application-and-deployment-manifests.md).

 El botón **seleccionar del almacén** permite seleccionar un certificado existente en el almacén de certificados personales del usuario actual. Puede seleccionar uno de estos certificados para firmar los manifiestos de aplicación e implementación.

 Haga clic en **Seleccionar de almacén** para abrir el cuadro de diálogo **Seleccionar un certificado**, donde se muestran los certificados del almacén de certificados personal que son válidos en la actualidad (no expirados) y que tienen claves privadas. El propósito del certificado seleccionado debe incluir la firma de código.

 Si hace clic en **Ver propiedades del certificado**, aparece el cuadro de diálogo **Detalles del certificado**. Este cuadro de diálogo incluye información detallada sobre el certificado y opciones adicionales. Puede hacer clic en **Más información sobre certificados** para ver información adicional de la Ayuda.

 El botón **seleccionar desde archivo** permite seleccionar un certificado de un archivo de clave existente.

 Haga clic en **Seleccionar de archivo** para abrir el cuadro de diálogo **Seleccionar archivo**, que permite seleccionar un archivo de clave de certificado (.pfx). El archivo debe estar protegido mediante contraseña y aún no puede estar en el almacén de certificados personal.

 En el cuadro de diálogo **Escribir contraseña para abrir archivo**, escriba una contraseña para abrir el archivo de clave de certificado (.pfx). La información de contraseña se almacena en la lista del contenedor de claves personal y en el almacén de certificados personal.

 El botón **crear certificado de prueba** le permite crear un certificado para realizar pruebas. El certificado de prueba se usa para firmar los manifiestos de aplicación e implementación de ClickOnce.

 Haga clic en **Crear certificado de prueba** para abrir el cuadro de diálogo **Crear certificado de prueba**, donde puede escribir una contraseña para el archivo de clave con nombre seguro del certificado de prueba. El archivo se denomina *nombreDeProyecto*_TemporaryKey.pfx. Si hace clic en **Aceptar** sin escribir una contraseña, el archivo .pfx no se cifra con contraseña.

 Cuadro de **dirección URL del servidor de marca** de tiempo especifica la dirección de un servidor que marca la firma como una marca de tiempo. Si se proporciona un certificado, este sitio externo comprueba la hora en que se ha firmado la aplicación.

## <a name="assembly-signing"></a>Firma de ensamblados
 Casilla **firmar el ensamblado** Active esta casilla para firmar el ensamblado y crear un archivo de clave con nombre seguro. Para obtener más información sobre la firma del ensamblado mediante el **Diseñador de proyectos**, vea [Cómo: Firmar un ensamblado (Visual Studio)](https://msdn.microsoft.com/f468a7d3-234c-4353-924d-8e0ae5896564).

 Esta opción usa la herramienta Al.exe proporcionada por [!INCLUDE[winsdklong](../../includes/winsdklong-md.md)] para firmar el ensamblado. Para obtener más información sobre Al.exe, vea [Cómo: Firmar un ensamblado con un nombre seguro](https://msdn.microsoft.com/library/2c30799a-a826-46b4-a25d-c584027a6c67).

 **Elegir una lista de archivo de clave de nombre seguro** permite especificar un archivo de clave con nombre seguro nuevo o existente que se usa para firmar el ensamblado. Seleccione **\<Browse...>** para seleccionar un archivo de clave existente.

 Seleccione **\<New...>** para crear un archivo de clave para firmar el ensamblado. Aparece el cuadro de diálogo **Crear clave de nombre seguro**, que se puede usar para especificar un nombre de archivo de clave y proteger el archivo de clave con una contraseña. La contraseña debe tener al menos 6 caracteres. Si especifica una contraseña, se crea un archivo de intercambio de información personal (.pfx); si no especifica ninguna contraseña, se crea un archivo de clave con nombre seguro (.snk).

 Botón **Cambiar contraseña** cambia la contraseña del archivo de clave de intercambio de información personal (. pfx) que se usa para firmar el ensamblado.

 Haga clic en **Cambiar contraseña** para abrir el cuadro de diálogo **Cambiar contraseña de clave**. En este cuadro de diálogo, **Contraseña anterior** es la contraseña actual del archivo de clave. **Nueva contraseña** debe tener al menos 6 caracteres. La información de contraseña se almacena en el almacén de certificados de Windows del usuario actual.

 Casilla **retrasar solo firma** Active esta casilla para habilitar la firma retardada.

 Tenga en cuenta que un proyecto con firma retardada no se ejecutará y no se puede depurar. Pero puede usar [Sn.exe (Herramienta de nombre seguro)](https://msdn.microsoft.com/library/c1d2b532-1b8e-4c7a-8ac5-53b801135ec6) con la opción `-Vr` para omitir la comprobación durante el desarrollo.

> [!NOTE]
> Al firmar un ensamblado, es posible que no siempre tenga acceso a una clave privada. Por ejemplo, una organización podría tener un par de claves muy bien guardado al que los desarrolladores no tuvieran acceso cada día. La clave pública podría estar disponible, pero el acceso a la clave privada estaría restringido a algunas personas. En tal caso, podría usar la *firma retardada* o la *firma parcial* para proporcionar la clave pública, retrasando la adición de la clave privada hasta la entrega del ensamblado.

## <a name="see-also"></a>Consulte también
 [Referencia de las propiedades del proyecto](../../ide/reference/project-properties-reference.md) administrar la firma de [ensamblados y manifiestos](../../ide/managing-assembly-and-manifest-signing.md) [firma de nombre seguro para aplicaciones administradas](https://msdn.microsoft.com/5fef3490-c519-4363-94fd-8b1ad260dab5) [Cómo: firmar manifiestos de aplicación e implementación](../../ide/how-to-sign-application-and-deployment-manifests.md) [Cómo: firmar un ensamblado (Visual Studio)](https://msdn.microsoft.com/f468a7d3-234c-4353-924d-8e0ae5896564) [Cómo: firmar un ensamblado con un nombre seguro](https://msdn.microsoft.com/library/2c30799a-a826-46b4-a25d-c584027a6c67) [ensamblados](https://msdn.microsoft.com/library/d4a80263-f3e0-4d81-9b61-f0cbeae3797b) con nombre seguro
