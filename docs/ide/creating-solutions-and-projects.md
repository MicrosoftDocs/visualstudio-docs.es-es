---
title: Crear soluciones y proyectos | Microsoft Docs
ms.custom: 
ms.date: 03/21/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.openprojectfromweb
- vs.newproject
- VS.ToolsOptionsPages.Projects.General
- SolutionItemsProject
helpviewer_keywords:
- solutions [Visual Studio], deleting
- solutions [Visual Studio], creating
- projects [Visual Studio], creating
ms.assetid: 836f8ca0-3fc9-4f4b-9090-45f2e4d2e9c8
caps.latest.revision: 46
author: kempb
ms.author: kempb
manager: ghogen
ms.translationtype: Human Translation
ms.sourcegitcommit: 5ea9179ad37514ffad4876177b05150eecc22def
ms.openlocfilehash: 9a4b04dc59c409a5c68ad1fb376abb33b3859ff6
ms.contentlocale: es-es
ms.lasthandoff: 05/24/2017

---

# Crear soluciones y proyectos
<a id="create-solutions-and-projects" class="xliff"></a>

Los proyectos son los contenedores lógicos de todo lo necesario para compilar la aplicación. Cuando se crea un proyecto mediante **Archivo**, **Nuevo**, **Proyecto** en el menú principal, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] crea una solución que lo contiene. Después puede agregar otros proyectos nuevos o existentes a la solución si fuese necesario. Puede crear proyectos a partir de archivos de código existentes, así como proyectos temporales (solo .NET) que se eliminarán cuando ya no los necesite.

> [!NOTE]
>  Las descripciones de este tema se basan en Visual Studio Community. Los cuadros de diálogo y los comandos de menú que se ven pueden diferir de los aquí descritos, en función de la configuración o la edición de Visual Studio. Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas** . Para más información, vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## Crear un proyecto a partir de una plantilla de proyecto instalada
<a id="create-a-project-from-an-installed-project-template" class="xliff"></a>  
 Seleccione **Archivo**, **Nuevo**, **Proyecto** en el menú principal para mostrar el cuadro de diálogo Nuevo proyecto. En el panel izquierdo, en **Instalado**, **Plantillas**, seleccione el lenguaje de programación y la plataforma o la tecnología y, después, elija una de las plantillas disponibles en el panel central.  

 En el diálogo **Nuevo proyecto** , el menú desplegable **Solución** le ofrece la opción de crear el nuevo proyecto en una solución nueva o existente, o en una nueva instancia de Visual Studio.  

## Crear un proyecto a partir de archivos de código existentes
<a id="create-a-project-from-existing-code-files" class="xliff"></a>  
 Si tiene una colección de archivos de origen separados, puede crear fácilmente un proyecto que los contenga. Seleccione **Archivo**, **Nuevo**, **Proyecto a partir de código existente** para iniciar el **Asistente para crear proyectos a partir de archivos de código existentes** y siga las indicaciones.  

> [!TIP]
>  Esta opción funciona mejor con recopilaciones de archivos relativamente simples.  

## Crear un proyecto temporal (C# y Visual Basic)
<a id="create-a-temporary-project-c-and-visual-basic" class="xliff"></a>
 Cuando se trabaja con proyectos temporales, puede crear y experimentar con un proyecto .NET sin especificar una ubicación de disco. Al crear un proyecto, basta con seleccionar un tipo de proyecto y una plantilla y especificar un nombre en el cuadro de diálogo **Nuevo proyecto** . Cuando trabaje con el proyecto temporal, podrá guardarlo o descartarlo en cualquier momento.  

## Crear un proyecto .NET que tenga como destino una versión concreta de .NET Framework
<a id="create-a-net-project-that-targets-a-specific-version-of-the-net-framework" class="xliff"></a>  
 Puede crear un proyecto que tenga como destino versiones anteriores de .NET Framework mediante el menú desplegable de versión **.NET Framework** que se encuentra en la parte superior del cuadro de diálogo **Nuevo proyecto** . Establezca este valor antes de seleccionar una plantilla de proyecto, dado que en la lista solo aparecerán plantillas compatibles con esa versión de .NET Framework.  

 Para obtener acceso a versiones anteriores a la 4, debe tener instalado .NET Framework 3.5 en su sistema.  

## Descargar soluciones de ejemplo
<a id="download-sample-solutions" class="xliff"></a>  
 Puede usar Visual para descargar e instalar soluciones de ejemplo desde la [Galería de código de MSDN](http://go.microsoft.com/fwlink/?LinkId=254185) y desde otros orígenes, como repositorios GIT.

 Puede descargar los ejemplos individualmente o puede descargar un Sample Pack, que contiene ejemplos relacionados que comparten una tecnología o un tema. Recibirá una notificación cuando se publiquen cambios en el código fuente de cualquier ejemplo que descargue.  

 Para obtener más información, vea [Ejemplos de Visual Studio](../ide/visual-studio-samples.md).  

## Agregar archivos individuales al nivel de solución
<a id="add-single-files-at-the-solution-level" class="xliff"></a>  
 A veces, puede tener un archivo al que hagan referencia varios proyectos, o que contenga texto o datos varios que, lógicamente, pertenezcan al nivel de solución en lugar de a un proyecto determinado.  Para agregar un solo elemento a una solución:  

- Haga clic con el botón derecho en el nodo de la solución en el **Explorador de soluciones** y seleccione **Agregar**, **Nuevo elemento** o **Agregar**, **Elemento existente**.  

## Crear soluciones vacías
<a id="create-empty-solutions" class="xliff"></a>  
 Aunque los proyectos pueden residir en una solución, puede crear soluciones que no contengan ningún proyecto. También puede abrir proyectos de código sin necesidad de una solución.

#### Para crear una solución vacía
<a id="to-create-an-empty-solution" class="xliff"></a>  

1.  En el menú **Archivo**, seleccione **Nuevo**, **Nuevo proyecto**.  

2.  En el panel izquierdo, seleccione **Instalado**, **Otros tipos de proyectos** y **Soluciones de Visual Studio** en la lista expandida.  

3.  En el panel central, seleccione **Solución en blanco**.  

4.  Establezca los valores **Nombre** y **Ubicación** de la solución y haga clic en **Aceptar**.  

Después de crear una solución vacía, puede agregarle elementos o proyectos nuevos o existentes al seleccionar **Agregar nuevo elemento** o **Agregar elemento existente** en el menú **Proyecto**.

### Eliminar soluciones
<a id="delete-solutions" class="xliff"></a>  
 Es posible eliminar una solución de forma permanente, pero sin usar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Antes de eliminar una solución, mueva cualquier proyecto que podría desear utilizar de nuevo en otra solución. A continuación, use el Explorador de archivos para eliminar el directorio que contiene los archivos de solución .sln y .suo.  

> [!NOTE]
>  El archivo .suo es un archivo oculto que no aparece en la configuración predeterminada del Explorador de archivos.  

##### Para eliminar una solución
<a id="to-delete-a-solution" class="xliff"></a>  

1.  En el **Explorador de soluciones**, en el menú contextual (clic con el botón derecho) de la solución que quiere eliminar, seleccione **Abrir carpeta en el Explorador de archivos**.

2.  Suba un nivel en el Explorador de archivos.

3.  Seleccione el directorio que contiene la solución y presione la tecla Suprimir.

## Vea también
<a id="see-also" class="xliff"></a>  
 [Soluciones y proyectos](../ide/solutions-and-projects-in-visual-studio.md)   

