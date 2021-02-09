---
title: 'Tutorial: publicar una extensión de Visual Studio | Microsoft Docs'
description: Obtenga información sobre cómo publicar una extensión de Visual Studio en Visual Studio Marketplace, que permite a los desarrolladores buscar extensiones nuevas y actualizadas.
ms.custom: SEO-VS-2020
ms.date: 01/15/2021
ms.topic: how-to
helpviewer_keywords:
- publishing web controls
- web controls, publishing
ms.assetid: a7816161-0490-4043-86f5-0f7331ed83b3
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: bda44c0c3f6c4b1986fc45a7c9cbf5c4ffa83043
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99889010"
---
# <a name="walkthrough-publish-a-visual-studio-extension"></a>Tutorial: publicar una extensión de Visual Studio

En este tutorial se muestra cómo publicar una extensión de Visual Studio en Visual Studio Marketplace. Al agregar la extensión a Visual Studio Marketplace, los desarrolladores pueden usar **extensiones y actualizaciones** para buscar extensiones nuevas y actualizadas.

## <a name="prerequisites"></a>Requisitos previos

 Para seguir este tutorial, debe instalar SDK de Visual Studio. Para obtener más información, vea [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-visual-studio-extension"></a>Crear una extensión de Visual Studio

En este artículo se usa una extensión VSPackage predeterminada, pero los pasos son válidos para cada tipo de extensión.

- Cree un VSPackage en C# denominado `TestPublish` que tenga un comando de menú. Para obtener más información, consulte [crear la primera extensión: Hola mundo](../extensibility/extensibility-hello-world.md).

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

## <a name="publish-the-extension-to-visual-studio-marketplace"></a>Publicar la extensión en Visual Studio Marketplace

1. Asegúrese de que ha creado la versión de lanzamiento de la extensión y de que está actualizada.

2. En un explorador Web, vaya a [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs).

3. En la esquina superior derecha, haga clic en **iniciar sesión**.

4. Para ello, use la cuenta de Microsoft. Si no tiene un cuenta Microsoft, puede crear uno en este momento.

5. Haga clic en **publicar extensiones**. Esta opción le lleva a la página de administración de todas las extensiones. Si no tiene una cuenta de publicador, se le pedirá que cree una en este momento.

   ![Cargar en Marketplace](media/upload-to-marketplace.png)

6. Elija el publicador que quiere usar para cargar la extensión. Puede cambiar los publicadores haciendo clic en los nombres de publicador que aparecen a la izquierda. Haga clic en **nueva extensión** y seleccione **Visual Studio**.

7. En **1: cargar la extensión**, puede elegir cargar un archivo VSIX directamente en Visual Studio Marketplace o simplemente agregar un vínculo a su propio sitio Web. En este ejemplo, se carga la extensión *TestPublish. vsix* . Arrastre y coloque la extensión o use el vínculo **haga clic** para buscar el archivo. Busque la extensión en la carpeta \bin\Release del proyecto.  Haga clic en **Continue**.

8. En **2: proporcione los detalles** de la extensión, algunos campos se rellenan automáticamente desde el archivo *source. Extension. vsixmanifest* de la extensión. Encuentre más detalles sobre cada uno de los siguientes:

    * **Nombre interno** se usa en la dirección URL de la página de detalles de la extensión. Por ejemplo, la publicación de una extensión con el nombre de publicador "nombre" y la especificación del nombre interno como "My Extension" da como resultado una dirección URL de "Marketplace. VisualStudio \. com/items? itemname = nombre. extensión" para la página de detalles de la extensión.

    * **Nombre para mostrar** de la extensión. Este nombre se rellena automáticamente desde el archivo *source. Extension. vsixmanifest* .

    * Número de **versión** de la extensión que se va a cargar. Esta versión se rellena automáticamente desde el archivo *source. Extension. vsixmanifest* .

    * El identificador de **VSIX** es el identificador único que Visual Studio usa para la extensión. Este identificador es necesario si desea que la extensión se actualice automáticamente. Este identificador se rellena automáticamente desde el archivo *source. Extension. vsixmanifest* .

    * **Logotipo** que se usa para la extensión. Este logotipo se rellena automáticamente desde el archivo *source. Extension. vsixmanifest* , si se proporciona.

    * **Breve descripción** de lo que hace la extensión. Esta descripción se rellena automáticamente desde el archivo *source. Extension. vsixmanifest* .

    * **Información general** es un buen lugar para incluir capturas de pantallas e información detallada sobre lo que hace la extensión.

    * **Las versiones de Visual Studio compatibles** le permiten elegir en qué versiones de Visual Studio funcionará su extensión. La extensión solo se instala en esas versiones.

    * La **edición de Visual Studio compatible** permite elegir en qué ediciones de Visual Studio funcionará su extensión. La extensión solo se instala en esas ediciones.

    * **Tipo**. El tipo más común de extensión son **las herramientas**.

    * **Categorías**. Elija hasta tres que mejor se adapten a su extensión.

    * Las **etiquetas** son palabras clave que ayudan a los usuarios a encontrar la extensión. Las etiquetas pueden ayudar a aumentar la relevancia de búsqueda de las extensiones en Visual Studio Marketplace.

    * La **categoría de precios** es el costo de la extensión.

    * El **repositorio de código fuente** le permite compartir un vínculo con el código fuente con la comunidad.

    * **Permitir Q&a para la extensión** permite que los usuarios dejen preguntas en la página de entrada de la extensión.

9. Haga clic en **guardar & cargar**. Esta opción le llevará a la página de administración del publicador. La extensión aún no se ha publicado.

10. Para publicar la extensión, haga clic con el botón derecho en la extensión y seleccione **hacer público**. Para ver el aspecto que tendrá la extensión en Visual Studio Marketplace, seleccione **Ver extensión**. Para los números de adquisición, haga clic en **informes**. Para realizar cambios en la extensión, haga clic en **Editar**.

    ![Menú de entrada de extensión](media/extension-entry-menu.png)

11. Haga clic en **hacer público** y la extensión ahora es pública. Busque el Visual Studio Marketplace de la extensión.

## <a name="update-a-published-extension-in-visual-studio-marketplace"></a>Actualizar una extensión Publicada en Visual Studio Marketplace

Antes de empezar, asegúrese de que ha creado la nueva versión de lanzamiento de la extensión y de que está actualizada.

1.  En un explorador Web, vaya a [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs).

1.  En la esquina superior derecha, haga clic en **iniciar sesión** e inicie sesión con el cuenta Microsoft.

    :::image type="content" source="media/marketplace-upload-extension.png" alt-text="Captura de pantalla que muestra la selección de un archivo de extensión cargado en el explorador de archivos.":::

1.  Haga clic en **publicar extensiones** y, a continuación, elija el publicador que quiere usar para cargar la extensión actualizada.

    :::image type="content" source="media/marketplace-select-extension-version.png" alt-text="Captura de pantalla de Visual Studio Marketplace con el vínculo Publish Extensions resaltado.":::

1.  Junto a la extensión que desea actualizar, mantenga el mouse sobre los tres puntos horizontales y, a continuación, elija **Editar**.

    :::image type="content" source="media/marketplace-select-extension.png" alt-text="Captura de pantalla que muestra la elección de una extensión para editar.":::

1.  En **1: cargar la extensión**, después del nombre de archivo VSIX, haga clic en el icono de lápiz para editar la extensión publicada.

     :::image type="content" source="media/marketplace-edit-extension-details.png" alt-text="Captura de pantalla que muestra cómo hacer clic en el icono de lápiz para editar la extensión.":::

1.  Busque el archivo. VSIX de la extensión actualizada. Haga clic en el archivo y, a continuación, haga clic en **abrir**.

    Las cargas de extensión actualizadas.

    :::image type="content" source="media/marketplace-upload-extension-notification.png" alt-text="Captura de pantalla de una notificación de carga de archivo después de cargar una extensión editada.":::

1. En **2: proporcione los detalles** de la extensión, algunos detalles son de solo lectura para una actualización de extensión o se rellenan automáticamente desde el archivo *source. Extension. vsixmanifest* de la extensión. Aquí encontrará más información sobre los detalles de la extensión:

    - **Nombre interno** \* se usa en la dirección URL de la página de detalles de la extensión. Por ejemplo, la publicación de una extensión con el nombre de publicador "nombre" y la especificación del nombre interno como "My Extension" da como resultado una dirección URL de "marketplace.visualstudio.com/items?itemName=myname.myextension" para la página de detalles de la extensión.

    - **Nombre** \* para mostrar de la extensión. Este nombre se rellena automáticamente desde el archivo *source. Extension. vsixmanifest* .

    - **Versión** \* de número de la extensión que se va a cargar. Esta versión se rellena automáticamente desde el archivo *source. Extension. vsixmanifest* .

    - **identificador** \* de VSIX es el identificador único que Visual Studio usa para la extensión. Este identificador es necesario si desea que la extensión se actualice automáticamente. Este identificador se rellena automáticamente desde el archivo *source. Extension. vsixmanifest* .

    - **Logotipo** \* de que se utiliza para la extensión. Este logotipo se rellena automáticamente desde el archivo *source. Extension. vsixmanifest* , si se proporciona.

    - **Descripción breve** \* de lo que hace la extensión. Esta descripción se rellena automáticamente desde el archivo *source. Extension. vsixmanifest* .

    - **Información general** es un buen lugar para incluir capturas de pantallas e información detallada sobre lo que hace la extensión.

    - Versiones compatibles de **Visual Studio** \* le permite elegir en qué versiones de Visual Studio trabajará su extensión. La extensión solo se instala en esas versiones.

    - Edición de Visual **Studio compatible** \* permite elegir las ediciones de Visual Studio en las que trabajará la extensión. La extensión se instala solo en esas ediciones.

    - **Tipo**. El tipo más común de extensión son **las herramientas**.

    - **Categorías**. Elija hasta tres que mejor se adapten a su extensión.

    - Las **etiquetas** son palabras clave que ayudan a los usuarios a encontrar la extensión. Las etiquetas pueden ayudar a aumentar la relevancia de búsqueda de las extensiones en Visual Studio Marketplace.

    - La **categoría de precios** es el costo de la extensión.

    - El **repositorio de código fuente** le permite compartir un vínculo con el código fuente con la comunidad.

    - **Permitir Q&a para la extensión** permite que los usuarios dejen preguntas en la página de entrada de la extensión.

       \* No se puede cambiar este detalle para una actualización de extensión.

1. Haga clic en **guardar & cargar**. Esta opción le llevará a la página de administración del publicador. La extensión aún no se ha publicado.

1. Para publicar la extensión, haga clic con el botón derecho en la extensión y seleccione **hacer público**. Para ver el aspecto que tendrá la extensión en Visual Studio Marketplace, seleccione **Ver extensión**. Para los números de adquisición, haga clic en **informes**. Para realizar cambios en la extensión, haga clic en **Editar**.

## <a name="add-additional-users-to-manage-your-publisher-account"></a>Agregar usuarios adicionales para administrar su cuenta de publicador

Visual Studio Marketplace admite la concesión de permisos a usuarios adicionales para obtener acceso a una cuenta de publicador y administrarla.

1. Vaya a la cuenta de publicador a la que desea agregar usuarios adicionales.

2. Seleccione **miembros** y haga clic en **Agregar**.

   ![Agregar usuario adicional](media/add-users.png)

3. Después, puede especificar la dirección de correo electrónico del usuario que desea agregar y conceder el nivel de acceso adecuado en **seleccionar un rol**.  Puede elegir entre las siguientes opciones:

   * **Creador**: el usuario puede publicar extensiones, pero no puede ver ni administrar extensiones publicadas por otros usuarios.

   * **Lector**: el usuario puede ver las extensiones, pero no puede publicar ni administrar extensiones.

   * **Colaborador**: el usuario puede publicar y administrar extensiones, pero no puede editar la configuración del publicador ni administrar el acceso.

   * **Propietario**: el usuario puede publicar y administrar extensiones, editar la configuración del publicador y administrar el acceso.

## <a name="install-the-extension-from-visual-studio-marketplace"></a>Instale la extensión desde Visual Studio Marketplace

Ahora que se ha publicado la extensión, instálela en Visual Studio y pruébelo en ella.

1. En Visual Studio, en el menú **herramientas** , haga clic en **extensiones y actualizaciones**.

2. Haga clic en **en línea** y busque **TestPublish**.

3. Haga clic en **Descargar**. A continuación, se programa la instalación de la extensión.

4. Para completar la instalación, cierre todas las instancias de Visual Studio.

## <a name="remove-the-extension"></a>Eliminación de la extensión

Puede quitar la extensión de Visual Studio Marketplace y del equipo.

### <a name="to-remove-the-extension-from-visual-studio-marketplace"></a>Para quitar la extensión de Visual Studio Marketplace

1. Vaya a [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs).

2. En la esquina superior derecha, haga clic en **publicar** extensiones. Elija el publicador que usó para publicar **TestPublish**. Aparece la lista de **TestPublish** .

3. Haga clic con el botón derecho en la entrada de extensión y haga clic en **quitar**. Se le pedirá que confirme si desea quitar la extensión. Haga clic en **OK**.

### <a name="to-remove-the-extension-from-your-computer"></a>Para quitar la extensión del equipo

1. En Visual Studio, en el menú **herramientas** , haga clic en **extensiones y actualizaciones**.

2. Seleccione **TestPublish** y, a continuación, haga clic en **desinstalar**. A continuación, se programa la extensión para la desinstalación.

3. Para completar la desinstalación, cierre todas las instancias de Visual Studio.
