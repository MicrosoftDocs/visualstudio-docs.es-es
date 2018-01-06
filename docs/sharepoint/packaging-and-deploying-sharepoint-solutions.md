---
title: Empaquetar e implementar soluciones de SharePoint | Documentos de Microsoft
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- packaging [SharePoint development in Visual Studio]
- deploying [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, packaging and deploying
ms.assetid: 39072fa7-9f94-49c0-9a67-cbcce0147e61
caps.latest.revision: "34"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: c584e4951289cd813a0f1d6bcf14920bd9713436
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="packaging-and-deploying-sharepoint-solutions"></a>Empaquetar e implementar soluciones de SharePoint
  Normalmente, una solución de SharePoint se implementa en un servidor de SharePoint mediante un archivo de solución (.wsp) de paquete. Puede usar Visual Studio para organizar los elementos de proyecto de SharePoint en características y crear un paquete para implementar las características de SharePoint.  
  
 En este tema se proporciona la información siguiente:  
  
-   [Creación de características y paquetes](#Creating)  
  
-   [Compatibilidad con las herramientas de paquetes y características](#Tools)  
  
-   [Implementar soluciones de SharePoint](#Deploying)  
  
-   [Implementar archivos en soluciones de SharePoint](#DeployingFiles)  
  
##  <a name="Creating"></a>Creación de características y paquetes  
 Puede usar Visual Studio para agrupar elementos relacionados de SharePoint en un *característica*. Por ejemplo, una característica para una definición de lista de contactos puede incluir la instancia de lista y la definición de lista. Puede combinar estos dos elementos en una única característica para fines de implementación. Para obtener más información acerca de las características, vea [bloques de creación: características](http://go.microsoft.com/fwlink/?LinkID=169183).  
  
 A continuación, puede crear un paquete de solución de SharePoint (.wsp) para agrupar varias características, definiciones del sitio, ensamblados y otros archivos en un paquete único, que almacena los archivos en un formato que necesita SharePoint para implementar los archivos en el servidor. Para obtener más información, consulte [bloques de creación: soluciones](http://go.microsoft.com/fwlink/?LinkID=169186).  
  
##  <a name="Tools"></a>Compatibilidad con las herramientas de paquetes y características  
 Puede usar las herramientas de desarrollo de SharePoint en Visual Studio para organizar rápidamente los archivos de SharePoint en características y paquetes de soluciones para la implementación sea más fácil. Puede usar las herramientas siguientes para configurar el paquete de características y soluciones.  
  
-   Diseñador de características y Diseñador de paquetes.  
  
-   Explorador de empaquetado, una ventana de herramientas.  
  
-   Explorador de soluciones.  
  
### <a name="feature-designer-and-package-designer"></a>Diseñador de características y Diseñador de paquetes  
 Puede crear características, establecer ámbitos y marcar otras características como dependencias utilizando el Diseñador de características. El diseñador también muestra el archivo XML final que se describe cada característica. Para obtener más información, consulte [crear características de SharePoint](../sharepoint/creating-sharepoint-features.md).  
  
 La característica se aplican a un sitio Web específico o un grupo de sitios Web estableciendo su *ámbito* en el Diseñador de características. Si una característica se activa para un sitio Web en particular, la característica solo funciona en ese sitio Web determinado. Si una característica se activa para una colección de sitios, los elementos de la característica se aplican a la colección de todo el sitio. Para obtener más información, consulte [ámbito elemento](http://go.microsoft.com/fwlink/?LinkID=169189).  
  
 Si la característica depende de otras características, puede establecer un *dependencia de activación de características* para marcar las características dependientes antes de realizar la característica disponible. Una dependencia de activación de característica comprueba si las características dependientes ya están activadas en ese ámbito. Para obtener más información, consulte [dependencias de activación y el ámbito](http://go.microsoft.com/fwlink/?LinkID=169190).  
  
 En el Diseñador de paquetes, puede agrupar los elementos de SharePoint en un único paquete de solución y configurar si se debe restablecer el servidor Web durante la implementación. Para establecer el tipo de servidor de implementación, utilice el **propiedades** ventana. El diseñador también genera el archivo XML que describe el contenido del paquete. Para obtener más información, consulte [crear paquetes de soluciones de SharePoint](../sharepoint/creating-sharepoint-solution-packages.md).  
  
 Durante la implementación, se detiene el servicio de Internet Information Services (IIS) para copiar los archivos de solución en el servidor de SharePoint. Mediante el Diseñador de paquetes en Visual Studio, puede seleccionar si se debe reiniciar el servidor Web. Para configurar si la solución se implementa en un servidor Web front-end o un servidor de aplicaciones, use el **propiedades** ventana. Para obtener más información, consulte [Solution Element (Solution)](http://go.microsoft.com/fwlink/?LinkID=169191).  
  
### <a name="packaging-explorer"></a>Explorador de empaquetado  
 Para complementar el Diseñador de características y el Diseñador de paquetes, puede usar el Explorador de empaquetado para agrupar los archivos de SharePoint en características y paquetes. Además, puede ver la vista jerárquica del proyecto de SharePoint de paquete, las características, los elementos y archivos. El Explorador de empaquetado es una ventana de herramientas que puede usar para completar las tareas siguientes:  
  
-   Abrir archivos y elementos de proyecto de SharePoint.  
  
-   Arrastrar y colocar elementos de proyecto de SharePoint de una característica a otro.  
  
-   Arrastrar y colocar elementos de proyecto de SharePoint y las características de un paquete a otro.  
  
-   Agregar una nueva característica a un paquete.  
  
-   Abra el Diseñador de una característica o paquete.  
  
-   Validar características y paquetes.  
  
 Las herramientas de desarrollo de SharePoint en Visual Studio tienen reglas de validación para ayudar a garantizar que el paquete de solución tiene el formato correcto. Además, las reglas comprueban que el archivo de solución WSP puede ser implementado correctamente y se activa en un servidor de SharePoint. Para obtener más información acerca del esquema XML para características, vea [característica esquemas](http://go.microsoft.com/fwlink/?LinkID=169192).  
  
 Puede agregar reglas de validación de paquetes y características personalizada para el sistema de proyectos de SharePoint. Para obtener más información, consulte [Cómo: Create Custom Feature y reglas de validación de paquetes para soluciones de SharePoint](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).  
  
 Para obtener más información sobre el Explorador de empaquetado, vea [Cómo: agregar y quitar características y elementos de un paquete mediante el Explorador de empaquetado](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md).  
  
### <a name="solution-explorer"></a>Explorador de soluciones  
 Puede usar el Explorador de soluciones para navegar y abrir los archivos del proyecto de SharePoint. Utilice el menú contextual en el Explorador de soluciones para agregar características, receptores de eventos de características y recursos de características. Además, puede abrir los diseñadores de características y los diseñadores de paquetes para configurar las características y paquetes para la implementación.  
  
##  <a name="Deploying"></a>Implementar soluciones de SharePoint  
 Después de personalizar las características y paquetes en Visual Studio, puede crear un archivo .wsp para implementar en servidores de SharePoint. Puede usar Visual Studio para depurar y probar el archivo .wsp en el servidor de SharePoint en el equipo de desarrollo. Para obtener más información acerca de cómo implementar las soluciones de SharePoint en un servidor remoto de SharePoint, vea [implementar una solución](http://go.microsoft.com/fwlink/?LinkID=169194).  
  
 También puede personalizar los pasos de implementación en el equipo de desarrollo. Para obtener más información, consulte [actualizar paquetes de soluciones de SharePoint, publicación e implementación](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md).  
  
##  <a name="DeployingFiles"></a>Implementar archivos en soluciones de SharePoint  
 Normalmente, cuando se agrega un elemento de proyecto de SharePoint a la solución de SharePoint, todos los necesarios se incluyen los archivos. Archivos que pueden ser compilado (archivos de código) están integradas en el ensamblado de salida de la solución. Sin embargo, también tendrá que agregar no compilable archivos, por ejemplo, .xml, .txt o archivos de recursos a un proyecto de SharePoint. Estos archivos no se empaquetan de manera automática en la solución. Para asegurarse de que se empaquetan, agregue los archivos a una carpeta asignada o a un elemento de proyecto de SharePoint.  
  
 Archivos agregados a las carpetas asignadas se copian automáticamente en el subárbol de SharePoint cuando se implementa la solución. Archivos agregados a un elemento de proyecto de SharePoint se implementan en la ubicación que se especifica en el **ubicación de implementación** propiedad para cada archivo, que parcial se establece en función de la **tipo de implementación** propiedad. De forma predeterminada, el **tipo de implementación** es el valor de la propiedad **NoDeployment**, lo que significa que el archivo no se implementa con la solución. Debe establecer otro valor para la propiedad que se va a incluir el archivo en el paquete.  
  
 Por ejemplo, para agregar un archivo .xml a un proyecto de SharePoint, realice una de estas acciones:  
  
-   Agregar una carpeta de SharePoint "Diseños" asignado al proyecto. Este modo se crea en **el Explorador de soluciones** una carpeta denominada **diseños** que tiene una subcarpeta para el proyecto. Agregar el archivo .xml a la nueva subcarpeta. De forma predeterminada, el archivo se implementa en el sistema de archivos de SharePoint en... \TEMPLATE\LAYOUTS\\*nombre de la carpeta*\\. Para obtener información sobre cómo agregar las carpetas asignadas, vea [Cómo: agregar y quitar carpetas asignado](../sharepoint/how-to-add-and-remove-mapped-folders.md).  
  
-   Agregar el archivo .xml en la carpeta de un elemento de proyecto de SharePoint y, a continuación, cambie la **tipo de implementación** propiedad del archivo .xml de **NoDeployment** a otra configuración como **RootFile** o **ElementFile**. Adecuado **tipo de implementación** depende de la configuración en el archivo y el proyecto. Para obtener más información sobre la **tipo de implementación** valores de propiedad, vea [desarrollar soluciones de SharePoint](../sharepoint/developing-sharepoint-solutions.md).  
  
 Si un archivo agregado no se aplica a ningún proyecto específico de la solución, puede agregar un proyecto de SharePoint vacío a la solución y, a continuación, agregar los archivos adicionales a ella. Otra alternativa para implementar los archivos en SharePoint, especialmente para la base de datos de contenido, consiste en Agregar un módulo al proyecto y, a continuación, agregue los archivos para el módulo. Para obtener más información, consulte [mediante módulos para incluir archivos de la solución](../sharepoint/using-modules-to-include-files-in-the-solution.md).  
  
## <a name="see-also"></a>Vea también  
 [Desarrollar soluciones de SharePoint](../sharepoint/developing-sharepoint-solutions.md)   
 [Compilar y depurar soluciones de SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)  
  
  