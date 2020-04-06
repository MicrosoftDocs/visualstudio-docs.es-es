---
title: 'Tutorial: Publicación de una extensión de Visual Studio ( Visual Studio Extension) Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- publishing web controls
- web controls, publishing
ms.assetid: a7816161-0490-4043-86f5-0f7331ed83b3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a34260124baedeba297dbd64e8a2c1856b55ec5a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697138"
---
# <a name="walkthrough-publish-a-visual-studio-extension"></a>Tutorial: Publicar una extensión de Visual Studio

En este tutorial se muestra cómo publicar una extensión de Visual Studio en Visual Studio Marketplace. Al agregar la extensión a Marketplace, los desarrolladores pueden usar **Extensiones y actualizaciones** para buscar extensiones nuevas y actualizadas.

## <a name="prerequisites"></a>Prerrequisitos

 Para seguir este tutorial, debe instalar SDK de Visual Studio. Para obtener más información, vea [Instalar el SDK](../extensibility/installing-the-visual-studio-sdk.md)de Visual Studio .

## <a name="create-a-visual-studio-extension"></a>Crear una extensión de Visual Studio

En este artículo se usa una extensión de VSPackage predeterminada, pero los pasos son válidos para cada tipo de extensión.

1. Crear un VSPackage en `TestPublish` C- denominado que tiene un comando de menú. Para obtener más información, consulte [Crear la primera extensión: Hello World](../extensibility/extensibility-hello-world.md).

## <a name="package-your-extension"></a>Empaquetado de la extensión

1. Actualice la extensión *.vsixmanifest* con la información correcta sobre el nombre del producto, el autor y la versión.

   ![extensión de actualización vsixmanifest](media/update-extension-vsixmanifest.png)

2. Cree la extensión en el modo **de versión.** Ahora, la extensión se empaqueta como un VSIX en la carpeta .bin.Release.

3. Puede hacer doble clic en VSIX para comprobar la instalación.

## <a name="test-the-extension"></a>Pruebe la extensión

 Antes de distribuir la extensión, compílela y pruébela para asegurarse de que está instalada correctamente en la instancia experimental de Visual Studio.

1. En Visual Studio, inicie la depuración para abrir una instancia experimental de Visual Studio.

2. En la instancia experimental, vaya al menú **Herramientas** y haga clic en **Extensiones y actualizaciones**. La extensión TestPublish debe aparecer en el panel central y estar habilitada.

3. En el menú **Herramientas,** asegúrese de ver el comando test.

## <a name="publish-the-extension-to-the-visual-studio-marketplace"></a>Publique la extensión en Visual Studio Marketplace

1. Asegúrese de que ha creado la versión De lanzamiento de la extensión y de que está actualizada.

2. En un explorador web, abra el sitio web de [Visual Studio Marketplace.](https://marketplace.visualstudio.com/vs)

3. En la esquina superior derecha, haga clic **en Iniciar sesión**.

4. Para ello, use la cuenta de Microsoft. Si no tiene una cuenta Microsoft, puede crear una en este momento.

5. Haga clic en **Publicar extensiones**.  Esta opción le navega a la página de administración de todas las extensiones. Si no tiene una cuenta de editor, se le pedirá que cree una en este momento.

   ![Subir a Marketplace](media/upload-to-marketplace.png)

6. Elija el editor que desea utilizar para cargar la extensión. Puede cambiar los editores haciendo clic en los nombres de los editores que aparecen a la izquierda. Haga clic en **Nueva extensión** y seleccione **Visual Studio**.

7. En **1: Cargar extensión,** puede elegir cargar un archivo VSIX directamente en Visual Studio Marketplace o simplemente agregar un vínculo a su propio sitio web. En este ejemplo, se carga la extensión *TestPublish.vsix.* Arrastre y suelte la extensión o utilice el vínculo **de clic** para buscar el archivo. Busque la extensión en la carpeta de la versión de la carpeta de la versión de la carpeta .  Haga clic en **Continuar**.

8. En **2: Proporcionar detalles**de extensión, algunos campos se rellenan automáticamente desde el archivo *source.extension.vsixmanifest* desde la extensión. Encuentre más detalles sobre cada uno a continuación:

    * **Nombre interno** se utiliza en la dirección URL de la página de detalles de la extensión. Por ejemplo, publicar una extensión bajo el nombre del editor "myname" y especificar el nombre interno para\.que sea "my extension" da como resultado una dirección URL de "marketplace.visualstudio com/items?itemName-myname.myextension" para la página de detalles de la extensión.

    * **Mostrar nombre** de la extensión. Este nombre se rellena automáticamente desde el archivo *source.extension.vsixmanifest.*

    * Número de **versión** de la extensión que está cargando. Esta versión se rellena automáticamente desde el archivo *source.extension.vsixmanifest.*

    * **Identificador de VSIX** es el identificador único que Visual Studio usa para la extensión. Este identificador es necesario si desea que la extensión se actualice automáticamente. Este identificador se rellena automáticamente desde el archivo *source.extension.vsixmanifest.*

    * **Logotipo** que se utiliza para la extensión. Este logotipo se rellena automáticamente desde el archivo *source.extension.vsixmanifest* si se proporciona.

    * **Breve descripción** de lo que hace su extensión. Esta descripción se rellena automáticamente desde el archivo *source.extension.vsixmanifest.*

    * **Información general** es un buen lugar para incluir capturas de pantalla e información detallada sobre lo que hace su extensión.

    * **Las versiones compatibles** de Visual Studio le permiten elegir en qué versiones de Visual Studio funcionará la extensión. La extensión solo se instala en esas versiones.

    * **La edición de Visual Studio compatible le permite elegir en qué ediciones de Visual Studio funcionará la extensión. La extensión solo se instala en esas ediciones.

    * **Tipo**. Las extensiones más comunes son **Herramientas**.

    * **Categorías**. Elige hasta tres que sean los más adecuados para tu extensión.

    * **Las etiquetas** son palabras clave que ayudan a los usuarios a encontrar la extensión. Las etiquetas pueden ayudar a aumentar la relevancia de la búsqueda de las extensiones en Marketplace.

    * **Categoría de precios** es el costo de su extensión.

    * **El repositorio** de código fuente le permite compartir un vínculo a su código fuente con la comunidad.

    * **Permitir Q&A para su extensión** permite a los usuarios dejar preguntas en la página de entrada de la extensión.

9. Haga clic en **Guardar & Cargar**. Esta opción le lleva de nuevo a la página de administración del editor. Su extensión aún no se ha publicado. Para publicar la extensión, haga clic con el botón derecho en la extensión y seleccione **Hacer público**. Puede ver cómo se verá la extensión en Marketplace seleccionando **Ver extensión**. Para los números de adquisición, haga clic en **Informes**. Para realizar cambios en su extensión, haga clic en **Editar**.

   ![Menú de entrada de extensión](media/extension-entry-menu.png)

10. Después de hacer clic en **Hacer público**, la extensión ahora es pública. Busque la extensión en Visual Studio Marketplace.

## <a name="add-additional-users-to-manage-your-publisher-account"></a>Agregue usuarios adicionales para administrar su cuenta de editor

Marketplace admite la concesión de permisos de usuarios adicionales para acceder y administrar una cuenta de editor.

1. Vaya a la cuenta de editor a la que desea agregar usuarios adicionales.

2. Seleccione **Miembros** y haga clic en **Agregar**.

   ![Agregar usuario adicional](media/add-users.png)

3. A continuación, puede especificar la dirección de correo electrónico del usuario que desea agregar y conceder el nivel de acceso adecuado en **Seleccionar un rol**.  Puede elegir entre las siguientes opciones:

   * **Creador**: El usuario puede publicar extensiones, pero no puede ver ni administrar extensiones publicadas por otros usuarios.

   * **Lector:** el usuario puede ver las extensiones, pero no puede publicar ni administrar extensiones.

   * **Colaborador:** el usuario puede publicar y administrar extensiones, pero no puede editar la configuración del editor ni administrar el acceso.

   * **Propietario:** El usuario puede publicar y administrar extensiones, editar la configuración del editor y administrar el acceso.

## <a name="install-the-extension-from-the-visual-studio-marketplace"></a>Instale la extensión desde Visual Studio Marketplace

Ahora que se ha publicado la extensión, instálela en Visual Studio y pruébela allí.

1. En Visual Studio, en el menú **Herramientas** , haga clic en **Extensiones y actualizaciones**.

2. Haga clic en **En línea** y, a continuación, busque **TestPublish**.

3. Haga clic en **Descargar**. A continuación, la extensión se programa para su instalación.

4. Para completar la instalación, cierre todas las instancias de Visual Studio.

## <a name="remove-the-extension"></a>Eliminación de la extensión

Puede quitar la extensión de Visual Studio Marketplace y del equipo.

### <a name="to-remove-the-extension-from-the-visual-studio-marketplace"></a>Para quitar la extensión de Visual Studio Marketplace

1. Abra el sitio web de [Visual Studio Marketplace.](https://marketplace.visualstudio.com/vs)

2. En la esquina superior derecha, haga clic en **Publicar** extensiones. Elija el publicador que utilizó para publicar **TestPublish**. Aparece la lista de **TestPublish.**

3. Haga clic con el botón derecho en la entrada de extensión y haga clic en **Quitar**. Se le pedirá que confirme si desea eliminar la extensión. Haga clic en **OK**.

### <a name="to-remove-the-extension-from-your-computer"></a>Para eliminar la extensión del ordenador

1. En Visual Studio, en el menú **Herramientas** , haga clic en **Extensiones y actualizaciones**.

2. Seleccione **TestPublish** y, a continuación, haga clic en **Desinstalar**. A continuación, la extensión se programa para su desinstalación.

3. Para completar la desinstalación, cierre todas las instancias de Visual Studio.
