---
title: "Empaquetar e implementar soluciones de SharePoint | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "implementar [desarrollo de SharePoint en Visual Studio]"
  - "empaquetar [desarrollo de SharePoint en Visual Studio]"
  - "desarrollo de SharePoint en Visual Studio, empaquetado e implementación"
ms.assetid: 39072fa7-9f94-49c0-9a67-cbcce0147e61
caps.latest.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 33
---
# Empaquetar e implementar soluciones de SharePoint
  Normalmente, una solución de SharePoint se implementa en un servidor de SharePoint mediante un archivo \(.wsp\) de paquete de solución.  Puede utilizar Visual Studio para organizar sus Elementos de proyecto de SharePoint en características y crear un paquete para implementar las características de SharePoint.  
  
 En este tema se proporciona la información siguiente:  
  
-   [Crear características y paquetes](#Creating)  
  
-   [Compatibilidad con las herramientas de paquetes y características](#Tools)  
  
-   [Implementar soluciones de SharePoint](#Deploying)  
  
-   [Implementar los archivos en las soluciones de SharePoint](#DeployingFiles)  
  
##  <a name="Creating"></a> Crear características y paquetes  
 Puede utilizar Visual Studio para agrupar los elementos de SharePoint relacionados en una *característica*.  Por ejemplo, una característica para una definición de lista de Contactos puede incluir la instancia de la lista y la definición de la lista.  Puede combinar estos dos elementos en una característica única con fines de implementación.  Para obtener más información sobre las características, [Bloque de creación: Características](http://go.microsoft.com/fwlink/?LinkID=169183)vea.  
  
 A continuación, puede crear un paquete de solución de SharePoint \(.wsp\) para empaquetar varias características, definiciones del sitio, ensamblados y otros archivos en un paquete único que almacene los archivos en un formato que necesita SharePoint para implementar los archivos en el servidor.  Para obtener más información, vea [Bloque de creación: Soluciones](http://go.microsoft.com/fwlink/?LinkID=169186).  
  
##  <a name="Tools"></a> Compatibilidad con las herramientas de paquetes y características  
 Puede utilizar las herramientas de desarrollo de SharePoint en Visual Studio para organizar rápidamente los archivos de SharePoint en características y paquetes de solución de forma que la implementación sea más fácil.  Puede utilizar las siguientes herramientas para configurar las características y los paquetes de solución.  
  
-   Diseñador de características y Diseñador de paquetes.  
  
-   Explorador de empaquetado, una ventana de herramientas.  
  
-   Explorador de soluciones.  
  
### Diseñador de características y Diseñador de paquetes  
 Puede crear características, establecer ámbitos y marcar otras características como dependencias utilizando el Diseñador de características.  El diseñador también muestra el archivo XML final en el que se describe cada característica.  Para obtener más información, vea [Crear características de SharePoint](../sharepoint/creating-sharepoint-features.md).  
  
 Aplique la característica a un sitio web o grupo de sitios web concreto estableciendo su *ámbito* en el Diseñador de características.  Si una característica se activa para un sitio web individual, la característica solo trabaja en ese sitio web.  Si una característica se activa para una colección de sitios, los elementos de la característica se aplican a la colección de sitios entera.  Para obtener más información, vea [Ámbito del elemento](http://go.microsoft.com/fwlink/?LinkID=169189).  
  
 Si la característica depende de otras características, puede establecer una *dependencia de activación de característica* para marcar las características dependientes antes de que la característica pase a estar disponible.  Una dependencia de activación de característica comprueba si las características dependientes ya están activadas en ese ámbito.  Para obtener más información, vea [Dependencias y ámbito de activación](http://go.microsoft.com/fwlink/?LinkID=169190).  
  
 En el Diseñador de paquetes, puede agrupar los elementos de SharePoint en un único paquete de solución y configurar si se debe restablecer el servidor web durante la implementación.  Para establecer el tipo de servidor de implementación, utilice la ventana **Propiedades**.  El diseñador también genera el archivo XML que describe el contenido del paquete.  Para obtener más información, vea [Crear paquetes de soluciones de SharePoint](../sharepoint/creating-sharepoint-solution-packages.md).  
  
 Durante la implementación, el servicio de Internet Information Services \(IIS\) se detiene para copiar los archivos de solución en el servidor de SharePoint.  Utilizando el Diseñador de paquetes en Visual Studio, puede seleccionar si se debe reiniciar el servidor web.  Para configurar si la solución se implementa en un servidor web front\-end o un servidor de aplicaciones, use la ventana **Propiedades**.  Para obtener más información, vea [Elemento de la solución \(solución\)](http://go.microsoft.com/fwlink/?LinkID=169191).  
  
### Explorador de empaquetado  
 Como complemento del Diseñador de características y del Diseñador de paquetes puede utilizar el Explorador de empaquetado para agrupar los archivos de SharePoint en características y paquetes.  Además, puede ver la vista jerárquica del paquete, las características, los elementos de proyecto de SharePoint y los archivos.  El explorador de empaquetado es una ventana de herramientas que puede utilizar para completar las tareas siguientes:  
  
-   Abrir archivos y elementos de proyecto de SharePoint.  
  
-   Arrastrar y colocar elementos de proyecto de SharePoint de una característica en otra.  
  
-   Arrastrar y colocar elementos de proyecto y características de SharePoint de un paquete en otro.  
  
-   Agregar una nueva característica a un paquete.  
  
-   Abrir un diseñador de paquetes o de características.  
  
-   Validar características y paquetes.  
  
 Las herramientas de desarrollo de SharePoint en Visual Studio tienen reglas de validación que permiten asegurarse de que el paquete de solución tiene un formato correcto.  Además, las reglas comprueban si el archivo de solución .wsp puede implementarse y activarse correctamente en un servidor de SharePoint.  Para obtener más información sobre el esquema XML para las características, vea [Esquemas de características](http://go.microsoft.com/fwlink/?LinkID=169192).  
  
 Puede agregar reglas de validación de características y paquetes personalizadas al sistema de proyectos de SharePoint.  Para obtener más información, vea [How to: Create Custom Feature and Package Validation Rules for SharePoint Solutions](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).  
  
 Para obtener más información sobre el Explorador de empaquetado, vea [Cómo: Agregar y quitar características y elementos de un paquete con el explorador de empaquetado](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md).  
  
### Explorador de soluciones  
 Puede utilizar el Explorador de soluciones para navegar y abrir los archivos del proyecto de SharePoint.  Utilice el menú contextual en el Explorador de soluciones para agregar características, receptores de eventos de características y recursos de características.  Además, puede abrir los Diseñadores de características y de paquetes para configurar las características y los paquetes para la implementación.  
  
##  <a name="Deploying"></a> Implementar soluciones de SharePoint  
 Después de personalizar las características y los paquetes en Visual Studio, puede crear un archivo .wsp para implementar en servidores de SharePoint.  Puede utilizar Visual Studio para depurar y probar el archivo .wsp solo en el servidor de SharePoint del equipo de desarrollo.  Para obtener más información sobre cómo implementar soluciones de SharePoint en un servidor remoto de SharePoint, vea [Implementar una solución](http://go.microsoft.com/fwlink/?LinkID=169194).  
  
 También puede personalizar los pasos de implementación en el equipo de desarrollo.  Para obtener más información, vea [Implementar, publicar y actualizar paquetes de soluciones de  
SharePoint](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md).  
  
##  <a name="DeployingFiles"></a> Implementar los archivos en las soluciones de SharePoint  
 Normalmente, al agregar un elemento de proyecto de SharePoint a la solución de SharePoint, están incluidos todos los archivos necesarios.  Los archivos que se pueden compilar \(archivos de código\) se integran en el ensamblado de salida de la solución.  Sin embargo, también puede ser necesario agregar los archivos no compilables, por ejemplo, .xml, .txt o archivos de recursos, a un proyecto de SharePoint.  Estos archivos no se empaquetan automáticamente en la solución.  Para asegurarse de que se empaquetan, agregue los archivos a una carpeta asignada o a un elemento de proyecto de SharePoint.  
  
 Los archivos agregados a las carpetas asignadas se copian automáticamente al subárbol de SharePoint cuando se implementa la solución.  Los archivos agregados a un elemento de proyecto de SharePoint se implementan en la ubicación especificada en la propiedad **Ubicación de implementación** para cada archivo, que se establece parcialmente según el valor de propiedad **Tipo de implementación**.  De forma predeterminada, el valor de propiedad **Tipo de implementación** es **NoDeployment**, que significa que el archivo no se implementa con la solución.  Se debe establecer otro valor para que la propiedad incluya el archivo en el paquete.  
  
 Por ejemplo, para agregar un archivo .xml a un proyecto de SharePoint, realice una de estas acciones:  
  
-   Agregue una carpeta asignada "Layouts" de SharePoint al proyecto.  Esto crea en el **Explorador de soluciones** una carpeta denominada **Layouts** que contiene una subcarpeta para el proyecto.  Agregue el archivo.xml a la nueva subcarpeta:  De forma predeterminada, el archivo se implementa en el sistema de archivos de SharePoint en. \\ de*Folder Name*de \\TEMPLATE\\LAYOUTS\\.  Para obtener más información acerca de cómo agregar carpetas asignadas, vea [Cómo: Agregar y quitar carpetas asignadas](../sharepoint/how-to-add-and-remove-mapped-folders.md).  
  
-   Agregue el archivo .xml a la carpeta de un elemento de proyecto de SharePoint y, a continuación, cambie la propiedad **Tipo de implementación** del archivo .xml de **NoDeployment** a otro valor como **RootFile** o **ElementFile**.  El valor de **Tipo de implementación** adecuado depende del archivo y del proyecto.  Para obtener más información sobre los valores de las propiedades de **Tipo de implementación**, vea [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md).  
  
 Si un archivo agregado no se aplica a ningún proyecto concreto de la solución, puede agregar un proyecto de SharePoint vacío a la solución y, a continuación, agregarle los archivos adicionales.  Otra alternativa para implementar los archivos en SharePoint, sobre todo en la base de datos de contenido, consiste en agregar un módulo al proyecto y, a continuación, agregar los archivos al módulo.  Para obtener más información, vea [Utilizar módulos para incluir archivos en la solución](../sharepoint/using-modules-to-include-files-in-the-solution.md).  
  
## Vea también  
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)   
 [Compilar y depurar soluciones de SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)  
  
  