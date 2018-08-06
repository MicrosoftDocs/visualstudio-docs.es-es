---
title: 'Tutorial: Publicar una extensión de Visual Studio | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- publishing web controls
- web controls, publishing
ms.assetid: a7816161-0490-4043-86f5-0f7331ed83b3
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 80bf0d3885f9dc4e4360b8516bd13a62cfbea952
ms.sourcegitcommit: ef828606e9758c7a42a2f0f777c57b2d39041ac3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/06/2018
ms.locfileid: "39566809"
---
# <a name="walkthrough-publish-a-visual-studio-extension"></a>Tutorial: Publicar una extensión de Visual Studio

En este tutorial se muestra cómo publicar una extensión de Visual Studio en Visual Studio Marketplace. Cuando se agrega la extensión en Marketplace, los desarrolladores pueden usar **extensiones y actualizaciones** para buscar extensiones nuevas y actualizadas.

## <a name="prerequisites"></a>Requisitos previos

 Para seguir este tutorial, debe instalar el SDK de Visual Studio. Para obtener más información, consulte [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-visual-studio-extension"></a>Crear una extensión de Visual Studio

En este artículo usa una extensión predeterminada de VSPackage, pero los pasos son válidos para cada tipo de extensión.

1. Crear un VSPackage en C# llamado `TestPublish` que tiene un comando de menú. Para obtener más información, consulte [crear su primera extensión: Hola mundo](../extensibility/extensibility-hello-world.md).

## <a name="package-your-extension"></a>Empaquetar la extensión

1. Actualizar la extensión *.vsixmanifest* con la información sobre el nombre de producto, el autor y la versión correcta.

  ![actualizar extensión vsixmanifest](media/update-extension-vsixmanifest.png)

2. Compilar la extensión **versión** modo. Ahora la extensión se empaqueta como un archivo VSIX en la carpeta \bin\Release.

3. Hacer doble clic en el archivo VSIX para comprobar la instalación.

## <a name="test-the-extension"></a>Probar la extensión

 Antes de distribuir la extensión, compilarla y probarla para asegurarse de que está instalado correctamente en la instancia experimental de Visual Studio.

1. En Visual Studio, inicie la depuración para abrir una instancia experimental de Visual Studio.

2. En la instancia experimental, vaya a la **herramientas** menú y haga clic en **extensiones y actualizaciones**. La extensión TestPublish debe aparecer en el panel central y habilitarse.

3. En el **herramientas** menú, asegúrese de que ve el comando de prueba.

## <a name="publish-the-extension-to-the-visual-studio-marketplace"></a>Publicar la extensión de Visual Studio Marketplace

1. Asegúrese de que ha creado la versión de lanzamiento de la extensión y que está actualizada.

2. En un explorador web, abra el [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs) sitio Web.

3. En la esquina superior derecha, haga clic en **inicie sesión en**.

4. Para ello, use la cuenta de Microsoft. Si no tiene una cuenta de Microsoft, puede crear uno en este momento.

5. Haga clic en **publicar extensiones**.  Esta opción desplaza a la página de administración para todas sus extensiones. Si no tienes una cuenta de publicador, deberá crear uno en este momento.

  ![Cargar en Marketplace](media/upload-to-marketplace.png)

6. Elija el editor que desee utilizar para cargar la extensión. Puede cambiar los publicadores, haga clic en los nombres de publicador que aparecen a la izquierda. Haga clic en **nueva extensión** y seleccione **Visual Studio**.

7. En **1: cargar extensión**, puede elegir cargar un archivo VSIX directamente a Visual Studio Marketplace o agregar un vínculo a su propio sitio Web. En este ejemplo, la extensión, *TestPublish.vsix* se carga. Arrastre y coloque la extensión o use el **haga clic en** vínculo para buscar el archivo. Busque la extensión en la carpeta \bin\Release del proyecto.  Haga clic en **Continuar**.

8. En **2: proporcionar detalles de la extensión**, algunos campos están rellena automáticamente desde el *source.extension.vsixmanifest* archivo desde la extensión. Encontrar más detalles sobre cada una a continuación:

    * **Nombre interno** se usa en la dirección URL de página de detalles de la extensión. Para obtener un ejemplo, publicar una extensión en el nombre de publicador "MiNombre" y especificar el nombre interno para que sea "extensión my" da como resultado una dirección URL de "marketplace.visualstudio\.com/items?itemName=myname.myextension" para obtener información detallada de la extensión página.
    
    * **Nombre para mostrar** de su extensión. Este nombre es rellena automáticamente desde el *source.extension.vsixmanifest* archivo.
   
    * **Versión** número de la extensión que se va a cargar. Esta versión está rellena automáticamente desde el *source.extension.vsixmanifest* archivo.
    
    * **Id. de VSIX** es el identificador único que usa Visual Studio para la extensión. Este identificador es necesario si desea que tengan la extensión que se actualiza automáticamente. Este identificador es rellena automáticamente desde el *source.extension.vsixmanifest* archivo.
    
   * **Logotipo de** que se utiliza para la extensión. Este logotipo es rellena automáticamente desde el *source.extension.vsixmanifest* archivo si se proporciona.
    
    * **Descripción breve** de lo que hace la extensión. Esta descripción es rellena automáticamente desde el *source.extension.vsixmanifest* archivo.
    
    * **Información general sobre** es un buen lugar para incluir capturas de pantalla e información detallada sobre lo que hace la extensión.
    
    * **Versiones compatibles de Visual Studio** permite elegir qué versiones de Visual Studio funcionará la extensión en. Solo se instala la extensión para esas versiones.
    
    * ** Compatible de Visual Studio edition le permite elegir qué ediciones de Visual Studio funcionará la extensión en. Solo se instala la extensión para esas ediciones.
    
    * **Tipo**. El tipo más común de las extensiones son **herramientas**.
    
    * **Categorías**. Elija hasta tres son una mejor opción para la extensión.
    
    * **Etiquetas** son palabras clave que ayudan a los usuarios encontrar la extensión. Las etiquetas pueden ayudar a aumentar la relevancia de la búsqueda de las extensiones en Marketplace.
    
    * **Categoría de precios** es el costo de la extensión.
    
    * **Repositorio de código fuente** le permite compartir un vínculo al código fuente con la Comunidad.
    
    * **Permitir preguntas y respuestas para la extensión** permite a los usuarios dejar preguntas en la página de entrada de extensión.

9. Haga clic en **guardar y cargar**. Esta opción se retrocede para el publicador de la página de administración. Aún no se ha publicado la extensión. Para publicar su extensión, haga doble clic en la extensión y seleccione **hacer público**. Puede ver cómo la extensión sería en Marketplace seleccionando **ver extensión**. Para los números de adquisición, haga clic en **informes**. Para realizar cambios en la extensión, haga clic en **editar**.

  ![Menú de la entrada de extensión](media/extension-entry-menu.png)

10. Después de hacer clic **hacer público**, la extensión ahora es pública. Buscar para la extensión de Visual Studio Marketplace.

## <a name="add-additional-users-to-manage-your-publisher-account"></a>Agregar usuarios adicionales para administrar la cuenta de publicador

Marketplace admite la concesión de permisos de usuarios adicionales para acceder y administrar una cuenta de publicador.

1. Vaya a la cuenta de publicador que desea agregar usuarios adicionales.

2. Seleccione **miembros** y haga clic en **agregar**.

  ![Agregar usuarios adicionales](media/add-users.png)

3. A continuación, puede especificar la dirección de correo electrónico del usuario que desea agregar y conceder el nivel adecuado de acceso bajo **seleccionar un rol**.  Puede elegir entre las siguientes opciones:

  * **Creador**: el usuario puede publicar extensiones, pero no se puede ver o administrar extensiones publicadas por otros usuarios.
  
  * **Lector**: el usuario puede ver las extensiones, pero no se puede publicar o administrar extensiones.
  
  * **Colaborador**: el usuario puede publicar y administrar extensiones, pero no pueden editar la configuración del publicador ni administrar el acceso.
  
  * **Propietario**: el usuario puede publicar y administrar extensiones, editar la configuración del publicador y administrar el acceso.
  
## <a name="install-the-extension-from-the-visual-studio-marketplace"></a>Instalar la extensión de Visual Studio Marketplace

Ahora que se ha publicado la extensión, instalarlo en Visual Studio y pruébela.

1. En Visual Studio, en el **herramientas** menú, haga clic en **extensiones y actualizaciones**.

2. Haga clic en **Online** y, a continuación, busque **TestPublish**.

3. Haga clic en **Descargar**. Luego, la extensión está programada para instalación.

4. Para completar la instalación, cierre todas las instancias de Visual Studio.

## <a name="remove-the-extension"></a>Quitar la extensión

Puede quitar la extensión de Visual Studio Marketplace y de su equipo.

### <a name="to-remove-the-extension-from-the-visual-studio-marketplace"></a>Para quitar la extensión de Visual Studio Marketplace

1. Abra el [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs) sitio Web.

2. En la esquina superior derecha, haga clic en **publicar** extensiones. Seleccione el publicador que usó para publicar **TestPublish**. La lista de **TestPublish** aparece.

3. Haga doble clic en la entrada de extensión y haga clic en **quitar**. Se pide que confirme si desea quitar la extensión. Haga clic en **Aceptar**.

### <a name="to-remove-the-extension-from-your-computer"></a>Para quitar la extensión de su equipo

1. En Visual Studio, en el **herramientas** menú, haga clic en **extensiones y actualizaciones**.

2. Seleccione **TestPublish** y, a continuación, haga clic en **desinstalar**. La extensión, a continuación, está programada para desinstalarla.

3. Para completar la desinstalación, cierre todas las instancias de Visual Studio.
