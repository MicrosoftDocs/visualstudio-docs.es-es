---
title: 'Tutorial: publicar una extensión de Visual Studio | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- publishing web controls
- web controls, publishing
ms.assetid: a7816161-0490-4043-86f5-0f7331ed83b3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d6bd7a5d9622f7aea7382522dcf69ce660b61ae7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85904744"
---
# <a name="walkthrough-publish-a-visual-studio-extension"></a>Tutorial: publicar una extensión de Visual Studio

En este tutorial se muestra cómo publicar una extensión de Visual Studio en el Visual Studio Marketplace. Al agregar la extensión a Marketplace, los desarrolladores pueden usar **extensiones y actualizaciones** para buscar extensiones nuevas y actualizadas.

## <a name="prerequisites"></a>Requisitos previos

 Para seguir este tutorial, debe instalar SDK de Visual Studio. Para obtener más información, vea [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-visual-studio-extension"></a>Crear una extensión de Visual Studio

En este artículo se usa una extensión VSPackage predeterminada, pero los pasos son válidos para cada tipo de extensión.

1. Cree un VSPackage en C# denominado `TestPublish` que tenga un comando de menú. Para obtener más información, consulte [crear la primera extensión: Hola mundo](../extensibility/extensibility-hello-world.md).

## <a name="package-your-extension"></a>Empaquetado de la extensión

1. Actualice la extensión *. vsixmanifest* con la información correcta sobre el nombre del producto, el autor y la versión.

   ![actualizar vsixmanifest de extensión](media/update-extension-vsixmanifest.png)

2. Compilar la extensión en modo de **versión** . Ahora la extensión se empaqueta como VSIX en la carpeta \bin\Release

3. Puede hacer doble clic en VSIX para comprobar la instalación.

## <a name="test-the-extension"></a>Prueba de la extensión

 Antes de distribuir la extensión, compilarla y probarla para asegurarse de que se ha instalado correctamente en la instancia experimental de Visual Studio.

1. En Visual Studio, inicie la depuración para abrir una instancia experimental de Visual Studio.

2. En la instancia experimental, vaya al menú **herramientas** y haga clic en **extensiones y actualizaciones**. La extensión TestPublish debe aparecer en el panel central y estar habilitada.

3. En el menú **herramientas** , asegúrese de que ve el comando prueba.

## <a name="publish-the-extension-to-the-visual-studio-marketplace"></a>Publicar la extensión en el Visual Studio Marketplace

1. Asegúrese de que ha creado la versión de lanzamiento de la extensión y de que está actualizada.

2. En un explorador Web, abra el sitio Web [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs) .

3. En la esquina superior derecha, haga clic en **iniciar sesión**.

4. Para ello, use la cuenta de Microsoft. Si no tiene un cuenta de Microsoft, puede crear uno en este momento.

5. Haga clic en **publicar extensiones**.  Esta opción le lleva a la página de administración de todas las extensiones. Si no tiene una cuenta de publicador, se le pedirá que cree una en este momento.

   ![Cargar en Marketplace](media/upload-to-marketplace.png)

6. Elija el publicador que quiere usar para cargar la extensión. Puede cambiar los publicadores haciendo clic en los nombres de publicador que aparecen a la izquierda. Haga clic en **nueva extensión** y seleccione **Visual Studio**.

7. En **1: cargar la extensión**, puede elegir cargar un archivo VSIX directamente en Visual Studio Marketplace o simplemente agregar un vínculo a su propio sitio Web. En este ejemplo, se carga la extensión *TestPublish. vsix* . Arrastre y coloque la extensión o use el vínculo **haga clic** para buscar el archivo. Busque la extensión en la carpeta \bin\Release del proyecto.  Haga clic en **Continuar**.

8. En **2: proporcione los detalles**de la extensión, algunos campos se rellenan automáticamente desde el archivo *source. Extension. vsixmanifest* de la extensión. Encuentre más detalles sobre cada uno de los siguientes:

    * **Nombre interno** se usa en la dirección URL de la página de detalles de la extensión. Por ejemplo, la publicación de una extensión con el nombre de publicador "nombre" y la especificación del nombre interno como "My Extension" da como resultado una dirección URL de "Marketplace. VisualStudio \. com/items? itemname = nombre. extensión" para la página de detalles de la extensión.

    * **Nombre para mostrar** de la extensión. Este nombre se rellena automáticamente desde el archivo *source. Extension. vsixmanifest* .

    * Número de **versión** de la extensión que se va a cargar. Esta versión se rellena automáticamente desde el archivo *source. Extension. vsixmanifest* .

    * El identificador de **VSIX** es el identificador único que Visual Studio usa para la extensión. Este identificador es necesario si desea que la extensión se actualice automáticamente. Este identificador se rellena automáticamente desde el archivo *source. Extension. vsixmanifest* .

    * **Logotipo** que se usa para la extensión. Este logotipo se rellena automáticamente desde el archivo *source. Extension. vsixmanifest* , si se proporciona.

    * **Breve descripción** de lo que hace la extensión. Esta descripción se rellena automáticamente desde el archivo *source. Extension. vsixmanifest* .

    * **Información general** es un buen lugar para incluir capturas de pantallas e información detallada sobre lo que hace la extensión.

    * **Las versiones de Visual Studio compatibles** le permiten elegir en qué versiones de Visual Studio funcionará su extensión. La extensión solo se instala en esas versiones.

    * * * La edición de Visual Studio compatible permite elegir en qué ediciones de Visual Studio funcionará su extensión. La extensión solo se instala en esas ediciones.

    * **Tipo**. El tipo más común de extensiones son **las herramientas**.

    * **Categorías**. Elija hasta tres que mejor se adapten a su extensión.

    * Las **etiquetas** son palabras clave que ayudan a los usuarios a encontrar la extensión. Las etiquetas pueden ayudar a aumentar la relevancia de búsqueda de las extensiones en Marketplace.

    * La **categoría de precios** es el costo de la extensión.

    * El **repositorio de código fuente** le permite compartir un vínculo con el código fuente con la comunidad.

    * **Permitir Q&a para la extensión** permite que los usuarios dejen preguntas en la página de entrada de la extensión.

9. Haga clic en **guardar & cargar**. Esta opción le llevará a la página de administración del publicador. La extensión aún no se ha publicado. Para publicar la extensión, haga clic con el botón derecho en la extensión y seleccione **hacer público**. Puede ver el aspecto que tendrá su extensión en Marketplace seleccionando **Ver extensión**. Para los números de adquisición, haga clic en **informes**. Para realizar cambios en la extensión, haga clic en **Editar**.

   ![Menú de entrada de extensión](media/extension-entry-menu.png)

10. Después de hacer clic en **hacer público**, la extensión ahora es pública. Busque la extensión en el Visual Studio Marketplace.

## <a name="add-additional-users-to-manage-your-publisher-account"></a>Agregar usuarios adicionales para administrar su cuenta de publicador

Marketplace admite la concesión de permisos a otros usuarios para acceder a una cuenta de publicador y administrarla.

1. Vaya a la cuenta de publicador a la que desea agregar usuarios adicionales.

2. Seleccione **miembros** y haga clic en **Agregar**.

   ![Agregar usuario adicional](media/add-users.png)

3. Después, puede especificar la dirección de correo electrónico del usuario que desea agregar y conceder el nivel de acceso adecuado en **seleccionar un rol**.  Puede elegir entre las siguientes opciones:

   * **Creador**: el usuario puede publicar extensiones, pero no puede ver ni administrar extensiones publicadas por otros usuarios.

   * **Lector**: el usuario puede ver las extensiones, pero no puede publicar ni administrar extensiones.

   * **Colaborador**: el usuario puede publicar y administrar extensiones, pero no puede editar la configuración del publicador ni administrar el acceso.

   * **Propietario**: el usuario puede publicar y administrar extensiones, editar la configuración del publicador y administrar el acceso.

## <a name="install-the-extension-from-the-visual-studio-marketplace"></a>Instale la extensión desde el Visual Studio Marketplace

Ahora que se ha publicado la extensión, instálela en Visual Studio y pruébelo en ella.

1. En Visual Studio, en el menú **herramientas** , haga clic en **extensiones y actualizaciones**.

2. Haga clic en **en línea** y busque **TestPublish**.

3. Haga clic en **Descargar**. A continuación, se programa la instalación de la extensión.

4. Para completar la instalación, cierre todas las instancias de Visual Studio.

## <a name="remove-the-extension"></a>Eliminación de la extensión

Puede quitar la extensión del Visual Studio Marketplace y del equipo.

### <a name="to-remove-the-extension-from-the-visual-studio-marketplace"></a>Para quitar la extensión del Visual Studio Marketplace

1. Abra el sitio web de [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs) .

2. En la esquina superior derecha, haga clic en **publicar** extensiones. Elija el publicador que usó para publicar **TestPublish**. Aparece la lista de **TestPublish** .

3. Haga clic con el botón derecho en la entrada de extensión y haga clic en **quitar**. Se le pedirá que confirme si desea quitar la extensión. Haga clic en **OK**.

### <a name="to-remove-the-extension-from-your-computer"></a>Para quitar la extensión del equipo

1. En Visual Studio, en el menú **herramientas** , haga clic en **extensiones y actualizaciones**.

2. Seleccione **TestPublish** y, a continuación, haga clic en **desinstalar**. A continuación, se programa la extensión para la desinstalación.

3. Para completar la desinstalación, cierre todas las instancias de Visual Studio.
