---
title: Empaquetar e implementar soluciones de SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- packaging [SharePoint development in Visual Studio]
- deploying [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, packaging and deploying
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a50d7088cdeb868ef4170e3b4b76fbf129151626
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2019
ms.locfileid: "54867642"
---
# <a name="package-and-deploy-sharepoint-solutions"></a>Empaquetar e implementar soluciones de SharePoint
  Normalmente, una solución de SharePoint se implementa en un servidor de SharePoint mediante un archivo de paquete (.wsp) de la solución. Puede usar Visual Studio para organizar los elementos de proyecto de SharePoint en características y crear un paquete para implementar las características de SharePoint.  
  
 En este tema se proporciona la información siguiente:  
  
-   [Creación de características y paquetes](#Creating)  
  
-   [Compatibilidad con la herramienta de paquetes y características](#Tools)  
  
-   [Implementar soluciones de SharePoint](#Deploying)  
  
-   [Implementar archivos en soluciones de SharePoint](#DeployingFiles)  
  
## <a name="create-features-and-packages"></a>Creación de paquetes y características
 Puede usar Visual Studio para agrupar elementos relacionados de SharePoint en un *característica*. Por ejemplo, una característica para una definición de lista de contactos puede incluir la instancia de lista y la definición de lista. Puede combinar estos dos elementos en una sola característica para la implementación. Para obtener más información acerca de las características, consulte [bloques de creación: Características](http://go.microsoft.com/fwlink/?LinkID=169183).  
  
 A continuación, puede crear un paquete de solución de SharePoint (*.wsp*) para agrupar varias características, definiciones, ensamblados y otros archivos de sitio en un paquete único, que almacena los archivos en un formato que necesita SharePoint para implementar los archivos en el servidor. Para obtener más información, consulte [bloques de creación: Soluciones](http://go.microsoft.com/fwlink/?LinkID=169186).  
  
## <a name="feature-and-packaging-tool-support"></a>Características y compatibilidad con la herramienta de empaquetado
 Puede usar las herramientas de desarrollo de SharePoint en Visual Studio para organizar rápidamente los archivos de SharePoint en características y paquetes de soluciones para una implementación más sencilla. Puede usar las herramientas siguientes para configurar el paquete de características y soluciones.  
  
-   Diseñador de características y el Diseñador de paquetes.  
  
-   Explorador de empaquetado, una ventana de herramientas.  
  
-   Explorador de soluciones.  
  
### <a name="feature-designer-and-package-designer"></a>Diseñador de características y el Diseñador de paquetes
 Puede crear características, establecer ámbitos y marcar otras características como dependencias mediante el Diseñador de características. El diseñador también muestra el archivo XML final que se describe cada característica. Para obtener más información, consulte [las características de SharePoint crear](../sharepoint/creating-sharepoint-features.md).  
  
 Aplicar la característica a un sitio Web específico o un grupo de sitios Web estableciendo su *ámbito* en el Diseñador de características. Si se activa una característica para un sitio Web individual, la característica solo funciona en ese sitio Web. Si se activa una característica para una colección de sitios, los elementos de la característica se aplican a la colección de sitios todo. Para obtener más información, consulte [ámbito del elemento](http://go.microsoft.com/fwlink/?LinkID=169189).  
  
 Si la característica depende de otras características, puede establecer un *dependencia de activación de características* para marcar las características dependientes antes de realizar su función disponible. Una dependencia de activación de característica comprueba si las características dependientes ya están activadas en ese ámbito. Para obtener más información, consulte [dependencias de activación y el ámbito](http://go.microsoft.com/fwlink/?LinkID=169190).  
  
 En el Diseñador de paquetes, puede agrupar los elementos de SharePoint en un único paquete de solución y configurar si se debe restablecer el servidor Web durante la implementación. Para establecer el tipo de servidor de implementación, use el **propiedades** ventana. El diseñador también genera el archivo XML que describe el contenido del paquete. Para obtener más información, consulte [paquetes de solución de SharePoint crear](../sharepoint/creating-sharepoint-solution-packages.md).  
  
 Durante la implementación, se detiene el servicio de Internet Information Services (IIS) para copiar los archivos de solución en el servidor de SharePoint. Al usar el Diseñador de paquetes en Visual Studio, puede seleccionar si se debe reiniciar el servidor Web. Para configurar si la solución se implementa en un servidor Web front-end o un servidor de aplicaciones, use el **propiedades** ventana. Para obtener más información, consulte [elemento Solution (solución)](http://go.microsoft.com/fwlink/?LinkID=169191).  
  
### <a name="packaging-explorer"></a>Explorador de empaquetado  
 Para complementar el Diseñador de características y el Diseñador de paquetes, puede usar el Explorador de empaquetado para agrupar los archivos de SharePoint en características y paquetes. Además, puede ver la vista jerárquica del proyecto de SharePoint de paquete, las características, los elementos y los archivos. El Explorador de empaquetado es una ventana de herramientas que puede usar para completar las tareas siguientes:  
  
- Abrir archivos y elementos de proyecto de SharePoint.  
  
- Arrastre y coloque elementos de proyecto de SharePoint de una característica a otra.  
  
- Arrastre y coloque elementos de proyecto de SharePoint y las características de un paquete a otro.  
  
- Agregar una nueva característica a un paquete.  
  
- Abra el Diseñador de una característica o paquete.  
  
- Validar características y paquetes.  
  
  Las herramientas de desarrollo de SharePoint en Visual Studio tienen reglas de validación para ayudar a garantizar que el paquete de solución está formado correctamente. Además, las reglas comprueban que el *.wsp* archivo de solución se puede implementar y activar en un servidor de SharePoint correctamente. Para obtener más información acerca del esquema XML para las características, consulte [característica esquemas](http://go.microsoft.com/fwlink/?LinkID=169192).  
  
  Puede agregar la característica personalizada y las reglas de validación del paquete al sistema del proyecto de SharePoint. Para obtener más información, vea [Cómo: Creación de reglas de validación para las soluciones de SharePoint de características y paquetes](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).  
  
  Para obtener más información sobre el Explorador de empaquetado, vea [Cómo: Agregar y quitar características y elementos de un paquete mediante el Explorador de empaquetado](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md).  
  
### <a name="solution-explorer"></a>Explorador de soluciones
 Puede usar el Explorador de soluciones para navegar y abrir los archivos del proyecto de SharePoint. Use el menú contextual en el Explorador de soluciones para agregar características, receptores de eventos y los recursos de características. Además, puede abrir los diseñadores de características y los diseñadores de paquetes para configurar las características y paquetes para la implementación.  
  
## <a name="deploy-sharepoint-solutions"></a>Implementar soluciones de SharePoint
 Después de personalizar las características y paquetes en Visual Studio, puede crear un *.wsp* archivo para implementar servidores de SharePoint. Puede usar Visual Studio para depurar y probar el. *wsp* solo en el servidor de SharePoint en el equipo de desarrollo. Para obtener más información acerca de cómo implementar las soluciones de SharePoint en un servidor remoto de SharePoint, vea [implementar una solución](http://go.microsoft.com/fwlink/?LinkID=169194).  
  
 También puede personalizar los pasos de implementación en el equipo de desarrollo. Para obtener más información, consulte [implementar, publicar y actualizar paquetes de solución SharePoint](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md).  
  
## <a name="deploy-files-in-sharepoint-solutions"></a>Implementar archivos en soluciones de SharePoint
 Normalmente, cuando se agrega un elemento de proyecto de SharePoint para la solución de SharePoint, todos los necesarios se incluyen los archivos. Archivos que se pueden compilar (archivos de código) están integradas en el ensamblado de salida de la solución. Sin embargo, es posible que también deba agregar archivos que no es compilable, por ejemplo, *.xml*, *.txt*, o los archivos de recursos a un proyecto de SharePoint. Estos archivos no se empaquetan automáticamente en su solución. Para asegurarse de que se empaquetan, agregue los archivos en una carpeta asignada o a un elemento de proyecto de SharePoint.  
  
 Agregado archivos a las carpetas asignadas se copian automáticamente en el subárbol de SharePoint cuando se implementa la solución. Agregada archivos a un elemento de proyecto de SharePoint se implementan en la ubicación especificada en el **ubicación de implementación** según la propiedad para cada archivo, que es establecer parcialmente el **tipo de implementación** propiedad. De forma predeterminada, el **tipo de implementación** es el valor de propiedad **NoDeployment**, lo que significa que el archivo no se implementa con la solución. Debe establecer otro valor para la propiedad incluir el archivo en el paquete.  
  
 Por ejemplo, para agregar un *.xml* del archivo a un proyecto de SharePoint, lleve a cabo una de estas acciones:  
  
- Agregar una carpeta asignada de SharePoint "Diseños" al proyecto. Esto crea en **el Explorador de soluciones** una carpeta denominada **diseños** que tiene una subcarpeta para el proyecto. Agregar el *.xml* archivo a la nueva subcarpeta. De forma predeterminada, el archivo se implementa en el sistema de archivos de SharePoint en *... \TEMPLATE\LAYOUTS\\\<nombre de carpeta >*. Para obtener información sobre cómo agregar carpetas asignadas, vea [Cómo: agregar y quitar carpetas asignadas](../sharepoint/how-to-add-and-remove-mapped-folders.md).  
  
- Agregar el *.xml* archivo a la carpeta de un elemento de proyecto de SharePoint y, a continuación, cambie el **tipo de implementación** propiedad de la *.xml* desde **NoDeployment**  a otra configuración, como **RootFile** o **ElementFile**. Adecuado **tipo de implementación** configuración depende del archivo y el proyecto. Para obtener más información sobre la **tipo de implementación** valores de propiedad, vea [soluciones de desarrollo de SharePoint](../sharepoint/developing-sharepoint-solutions.md).  
  
  Si ha agregado el archivo no es aplicable a ningún proyecto específico de la solución, puede agregar un proyecto de SharePoint vacío a la solución y, a continuación, agregue los archivos adicionales a ella. Otra alternativa para implementar los archivos en SharePoint, especialmente a la base de datos de contenido, es agregar un módulo al proyecto y, a continuación, agregue los archivos para el módulo. Para obtener más información, consulte [utilizar módulos para incluir archivos en la solución](../sharepoint/using-modules-to-include-files-in-the-solution.md).  
  
## <a name="see-also"></a>Vea también
 [Desarrollar soluciones de SharePoint](../sharepoint/developing-sharepoint-solutions.md)   
 [Build and debug SharePoint solutions](../sharepoint/building-and-debugging-sharepoint-solutions.md) (Compilar y depurar las soluciones de SharePoint)  
