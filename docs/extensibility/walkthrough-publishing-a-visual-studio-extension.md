---
title: 'Tutorial: Publicar una extensión de Visual Studio | Documentos de Microsoft'
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
ms.openlocfilehash: f823334f3686bdba3406daac69b2a98d203780a7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-publishing-a-visual-studio-extension"></a>Tutorial: Publicar una extensión de Visual Studio

En este tutorial se muestra cómo publicar una extensión de Visual Studio en Visual Studio Marketplace. Cuando se agrega la extensión Marketplace, los desarrolladores pueden usar **extensiones y actualizaciones** para buscar allí extensiones nuevas y actualizadas.

## <a name="prerequisites"></a>Requisitos previos

 Para seguir este tutorial, debe instalar el SDK de Visual Studio. Para obtener más información, consulte [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-visual-studio-extension"></a>Crear una extensión de Visual Studio

En este caso se utilizará una extensión predeterminada de VSPackage, pero los mismos pasos son válidos para cada tipo de extensión.

1. Crear un VSPackage en C# llamado "TestPublish" que tiene un comando de menú. Para obtener más información, consulte [crear la primera extensión: Hello World](../extensibility/extensibility-hello-world.md).

## <a name="package-your-extension"></a>Empaquetar la extensión

1. Actualizar vsixmanifest extensión con la información correcta sobre el nombre del producto, autor y versión.

  ![actualizar la extensión vsixmanifest](media/update-extension-vsixmanifest.png)

2. Compilar la extensión **versión** modo. Ahora la extensión se empaquetarán como una extensión VSIX en la carpeta \bin\Release.

3. Puede hacer doble clic en VSIX para comprobar la instalación.

## <a name="test-the-extension"></a>Probar la extensión

 Antes de distribuir la extensión, compilar y probar para asegurarse de que está instalado correctamente en la instancia experimental de Visual Studio.

1. En Visual Studio, inicie la depuración. Para abrir una instancia experimental de Visual Studio.

2. En la instancia experimental, vaya a la **herramientas** menú y haga clic en **extensiones y actualizaciones...** . La extensión TestPublish debe aparecer en el panel central y habilitarse.

3. En el **herramientas** menú, asegúrese de que vea el comando de prueba.

## <a name="publish-the-extension-to-the-visual-studio-marketplace"></a>Publicar la extensión en el catálogo de soluciones de Visual Studio

1. Asegúrese de que ha generado la versión de lanzamiento de la extensión y que esté actualizada.

2. En un explorador web, abra el [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs) sitio Web.

3. En la esquina superior derecha, haga clic en **iniciar sesión en**.

4. Para ello, use la cuenta de Microsoft. Si no tiene una cuenta de Microsoft, puede crear uno en este momento.

5. Haga clic en **publicar extensiones**.  Esto le remitirá a la página de administración para todas las extensiones.  Si no tienes una cuenta de publicador, deberá crear uno en este momento.

  ![Cargar en Marketplace](media/upload-to-marketplace.png)

6. Elija el editor que desea utilizar para cargar la extensión.  Puede cambiar publicadores, haga clic en los nombres de publicador que aparecen a la izquierda.  Haga clic en **nueva extensión** y seleccione **Visual Studio**.

7. En **1: cargar la extensión**, puede cargar un archivo VSIX directamente en el catálogo de soluciones de Visual Studio o agregar un vínculo a su propio sitio Web. En este caso, se cargará la extensión, TestPublish.vsix.  Arrastre y coloque la extensión o bien use el **haga clic en** vínculo para buscar el archivo.  La extensión puede encontrarse en la carpeta \bin\Release del proyecto.  Haga clic en **Continuar**.

8. En **2: proporcionar detalles de la extensión**, algunos campos están rellena automáticamente desde el archivo source.extension.vsixmanifest de la extensión.  Encontrará más detalles sobre cada una a continuación:

    * **Nombre interno** se usará en la dirección URL de la página de detalles de la extensión. Para obtener un ejemplo, se producirán en una dirección URL de publicar una extensión en el nombre de publicador "myname" y especificando el nombre interno para que sea "myextension" "marketplace.visualstudio\.com/items?itemName=myname.myextension" para la extensión página de detalles.
    
    * **Nombre para mostrar** de la extensión.  Esto es rellena automáticamente desde el archivo source.extension.vsixmanifest.
   
    * **Versión** número de la extensión que se va a cargar.  Esto es rellena automáticamente desde el archivo source.extension.vsixmanifest.
    
    * **Identificador de VSIX** es el identificador único que Visual Studio usa para la extensión.  Esto es necesario si desea que tengan la extensión puede actualizar automáticamente.  Esto es rellena automáticamente desde el archivo source.extension.vsixmanifest.
    
   * **Logotipo de** que se usará para la extensión.  Esto se rellenarán automáticamente desde el archivo source.extension.vsixmanifest si se proporciona.
    
    * **Descripción breve de** de lo que hace la extensión.  Esto se rellenarán automáticamente desde el archivo source.extension.vsixmanifest.
    
    * **Información general sobre** es un buen lugar para incluir capturas de pantalla e información detallada sobre lo que hace la extensión.
    
    * **Admite versiones de Visual Studio** le permite seleccionar qué versiones de Visual Studio la extensión funcionarán en.  La extensión solo se instalará para esas versiones.
    
    * **Ediciones de Visual Studio compatibles** le permite seleccionar qué ediciones de Visual Studio la extensión se pueden usar en.  La extensión solo se instalará a esas ediciones.
    
    * **Tipo**.  El tipo más común de las extensiones están **herramientas**.
    
    * **Categorías**.  Seleccionar hasta tres que son una mejor se adapte a su extensión.
    
    * **Etiquetas** son palabras clave que ayudan a los usuarios buscar la extensión. Las etiquetas pueden ayudar a aumentar la relevancia de la búsqueda de las extensiones en el mercado.
    
    * **Precios de categoría** es el costo de la extensión.
    
    * **Repositorio de código fuente** le permite compartir un vínculo en el código fuente con la Comunidad.
    
    * **Permitir preguntas y respuestas para la extensión** permitirá a los usuarios dejar preguntas en la página de entrada de la extensión.

9. Haga clic en **guardar y cargar**. Esto le llevará página de administración de nuevo en el publicador.  Aún no se ha publicado la extensión.  Para publicar la extensión, haga doble clic en la extensión y seleccione **hacer público**.  Puede ver cómo la extensión será similar en Marketplace seleccionando **vista extensión**.  Para los números de adquisición, haga clic en **informes**.  Para realizar cambios en la extensión, haga clic en **editar*.

  ![Menú de la entrada de extensión](media/extension-entry-menu.png)

10. Después de hacer clic **hacer público**, la extensión es pública ahora.  Buscar en Visual Studio Marketplace para la extensión.

## <a name="add-additional-users-to-manage-your-publisher-account"></a>Agregar usuarios adicionales para administrar su cuenta de publicador

Marketplace admite la concesión de permisos de usuarios adicionales para acceder y administrar una cuenta de publicador.

1. Navegue a la cuenta del publicador que se va a agregar usuarios adicionales.

2. Seleccione **miembros** y haga clic en **agregar**

  ![Agregar usuarios adicionales](media/add-users.png)

3. A continuación, puede especificar la dirección de correo electrónico del usuario que se va a agregar y conceder el nivel adecuado de acceso en **seleccione un rol**.  Puede elegir entre las siguientes opciones:

  * **Creador**: el usuario puede publicar extensiones, pero no se puede ver o administrar las extensiones publicadas por otros usuarios.
  
  * **Lector**: el usuario puede ver las extensiones, pero no se puede publicar o administrar extensiones.
  
  * **Colaborador**: el usuario puede publicar y administrar extensiones, pero no se puede editar la configuración del publicador o administrar el acceso.
  
  * **Propietario**: el usuario puede publicar y administrar las extensiones, edite la configuración del publicador y administrar el acceso.
  
## <a name="install-the-extension-from-the-visual-studio-marketplace"></a>Instale la extensión desde el catálogo de soluciones de Visual Studio

Ahora que se publica la extensión, instalarlo en Visual Studio y pruébela.

1. En Visual Studio, en el **herramientas** menú, haga clic en **extensiones y actualizaciones...** .

2. Haga clic en **en línea** y, a continuación, busque TestPublish.

3. Haga clic en **Descargar**. A continuación, se programará para instalar la extensión.

4. Para completar la instalación, cierre todas las instancias de Visual Studio.

## <a name="remove-the-extension"></a>Quitar la extensión

Puede quitar la extensión de Visual Studio Marketplace y de su equipo.

### <a name="to-remove-the-extension-from-the-visual-studio-marketplace"></a>Para quitar la extensión de Visual Studio Marketplace

1. Abra la [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs) sitio Web.

2. En la esquina superior derecha, haga clic en **publicar** extensiones.  Seleccione el publicador que utiliza para publicar TestPublish.  Se muestra la lista de TestPublish.

3. Haga doble clic en la entrada de extensión y haga clic en **quitar** le pedirá que confirme si desea quitar la extensión.  Haga clic en **Aceptar**.

### <a name="to-remove-the-extension-from-your-computer"></a>Para quitar la extensión del equipo

1. En Visual Studio, en el **herramientas** menú, haga clic en **extensiones y actualizaciones...** .

2. Seleccione TestPublish y, a continuación, haga clic en **desinstalar**. A continuación, se programará la extensión para la desinstalación.

3. Para completar la desinstalación, cierre todas las instancias de Visual Studio.
