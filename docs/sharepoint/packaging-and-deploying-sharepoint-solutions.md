---
title: Empaquetado e implementación de soluciones de SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: overview
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
ms.openlocfilehash: 9a4bf3394cf47b4f355fbe6a330ff5374e2da1c9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "86015602"
---
# <a name="package-and-deploy-sharepoint-solutions"></a>Empaquetado e implementación de soluciones de SharePoint
  Normalmente, una solución de SharePoint se implementa en un servidor de SharePoint mediante un archivo de paquete de solución (.wsp). Puede usar Visual Studio para organizar los elementos de proyecto de SharePoint en características y crear un paquete para implementar las características de SharePoint.

 Este tema proporciona la siguiente información:

- [Creación de características y paquetes](#create-features-and-packages)

- [Compatibilidad con herramientas de empaquetado y características](#feature-and-packaging-tool-support)

- [Implementación de soluciones de SharePoint](#deploy-sharepoint-solutions)

- [Implementación de archivos en soluciones de SharePoint](#deploy-files-in-sharepoint-solutions)

## <a name="create-features-and-packages"></a>Creación de características y paquetes
 Puede usar Visual Studio para agrupar elementos de SharePoint relacionados en una *característica*. Por ejemplo, una característica para una definición de lista de contactos puede incluir la instancia de la lista y la definición de la lista. Puede combinar estos dos elementos en una sola característica con fines de implementación. Para obtener más información sobre las características, vea [Bloque de creación: Características](/previous-versions/office/developer/sharepoint-2010/ee537350(v=office.14)).

 Después, puede crear un paquete de solución de SharePoint ( *.wsp*) para agrupar varias características, definiciones de sitio, ensamblados y otros archivos en un único paquete, que almacena los archivos en un formato que SharePoint necesita para implementarlos en el servidor. Para obtener más información, vea [Bloque de creación: Soluciones](/previous-versions/office/developer/sharepoint-2010/ee537008(v=office.14)).

## <a name="feature-and-packaging-tool-support"></a>Compatibilidad con herramientas de empaquetado y características
 Puede usar las herramientas de desarrollo de SharePoint en Visual Studio para organizar rápidamente los archivos de SharePoint en características y paquetes de soluciones para facilitar la implementación. Puede usar las herramientas siguientes para configurar la característica y el paquete de la solución.

- Diseñador de características y Diseñador de paquetes.

- Explorador de empaquetado, una ventana de herramientas.

- Explorador de soluciones.

### <a name="feature-designer-and-package-designer"></a>Diseñador de características y Diseñador de paquetes
 Puede crear características, establecer ámbitos y marcar otras características como dependencias mediante el Diseñador de características. En el diseñador también se muestra el archivo XML final que describe cada característica. Para obtener más información, vea [Creación de características de SharePoint](../sharepoint/creating-sharepoint-features.md).

 Para aplicar la característica a un sitio web o grupo de sitios web específico, establezca su *ámbito* en el Diseñador de características. Si se activa una característica para un sitio web individual, la característica solo funciona en ese sitio web concreto. Si se activa una característica para una colección de sitios, los elementos de la característica se aplican a toda la colección de sitios. Para obtener más información, vea [Ámbito de elemento](/previous-versions/office/developer/sharepoint-2010/ms476615(v=office.14)).

 Si la característica se basa en otras, puede establecer una *dependencia de activación de características* para marcar las dependientes antes de que la característica esté disponible. Una dependencia de activación de características comprueba si las características dependientes ya están activadas en ese ámbito. Para obtener más información, vea [Dependencias de activación y ámbito](/previous-versions/office/developer/sharepoint-2010/aa543162(v=office.14)).

 En el Diseñador de paquetes, puede agrupar los elementos de SharePoint en un único paquete de solución y configurar si se debe restablecer el servidor web durante la implementación. Para establecer el tipo de servidor de implementación, use la ventana **Propiedades**. El diseñador también genera un archivo XML en el que se describe el contenido de cada paquete. Para obtener más información, vea [Creación de paquetes de solución de SharePoint](../sharepoint/creating-sharepoint-solution-packages.md).

 Durante la implementación, se detiene el servicio Internet Information Services (IIS) para copiar los archivos de solución en el servidor de SharePoint. Con el Diseñador de paquetes en Visual Studio, puede seleccionar si se debe reiniciar el servidor web. Para configurar si la solución se implementa en un servidor web de front-end o en un servidor de aplicaciones, use la ventana **Propiedades**. Para obtener más información, vea [Elemento de solución (solución)](/previous-versions/office/developer/sharepoint-2010/ms412929(v=office.14)).

### <a name="packaging-explorer"></a>Explorador de empaquetado
 Para complementar al Diseñador de características y al Diseñador de paquetes, puede usar el Explorador de empaquetado para agrupar los archivos de SharePoint en características y paquetes. Además, puede ver la vista jerárquica del paquete, las características, los elementos de proyecto de SharePoint y los archivos. El Explorador de empaquetado es una ventana de herramientas que puede usar para completar las tareas siguientes:

- Abrir elementos de proyecto y archivos de SharePoint.

- Arrastrar y colocar elementos de proyecto de SharePoint de una característica a otra.

- Arrastrar y colocar elementos de proyecto de SharePoint de un paquete característica a otro.

- Agregar una característica nueva a un paquete.

- Abrir el diseñador de una característica o un paquete.

- Validar características y paquetes.

  Las herramientas de desarrollo de SharePoint de Visual Studio disponen de reglas de validación para asegurarse de que el paquete de solución se crea de forma correcta. Además, las reglas comprueban que el archivo de solución *.wsp* se puede implementar y activar correctamente en un servidor de SharePoint. Para obtener más información sobre el esquema XML de las características, vea [Esquemas de características](/previous-versions/office/developer/sharepoint-2010/ms414322(v=office.14)).

  Puede agregar reglas personalizadas de validación de características y paquetes al sistema de proyectos de SharePoint. Para obtener más información, vea [Cómo: para crear reglas personalizadas de validación de características y paquetes para soluciones de SharePoint](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).

  Para obtener más información sobre el Explorador de empaquetado, vea [Procedimiento para agregar y quitar características y elementos de un paquete con el Explorador de empaquetado](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md).

### <a name="solution-explorer"></a>Explorador de soluciones
 Puede usar el Explorador de soluciones para navegar y abrir los archivos del proyecto de SharePoint. Use el menú contextual del Explorador de soluciones para agregar características, receptores de eventos de características y recursos de características. Además, puede abrir los diseñadores de características y de paquetes para configurar las características y los paquetes para la implementación.

## <a name="deploy-sharepoint-solutions"></a>Implementación de soluciones de SharePoint
 Después de personalizar las características y el paquete en Visual Studio, puede crear un archivo *.wsp* para implementarlo en los servidores de SharePoint. Puede usar Visual Studio para depurar y probar el archivo *.wsp* solo en el servidor de SharePoint del equipo de desarrollo. Para obtener más información sobre cómo implementar las soluciones de SharePoint en un servidor de SharePoint remoto, vea [Implementación de una solución](/previous-versions/office/developer/sharepoint-2010/aa544500(v=office.14)).

 También puede personalizar los pasos de implementación en el equipo de desarrollo. Para obtener más información, vea [Implementación, publicación y actualización de paquetes de soluciones de SharePoint](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md).

## <a name="deploy-files-in-sharepoint-solutions"></a>Implementación de archivos en soluciones de SharePoint
 Normalmente, al agregar un elemento de proyecto de SharePoint a la solución de SharePoint, se incluyen todos los archivos necesarios. Los archivos que se pueden compilar (archivos de código) se integran en el ensamblado de salida de la solución. Pero es posible que también tenga que agregar a un proyecto de SharePoint archivos que no se pueden compilar, por ejemplo, *.xml*, *.txt* o de recursos. Estos archivos no se empaquetan automáticamente en la solución. Para asegurarse de se empaqueten, agregue los archivos a una carpeta asignada o a un elemento de proyecto de SharePoint.

 Los archivos que se agregan a carpetas asignadas se copian de forma automática en el subárbol de SharePoint cuando se implementa la solución. Los archivos que se agregan a un elemento de proyecto de SharePoint se implementan en la ubicación que se especifica en la propiedad **Ubicación de implementación** de cada archivo, que se establece parcialmente en función de la propiedad **Tipo de implementación**. De forma predeterminada, el valor de la propiedad **Tipo de implementación** es **NoDeployment**, lo que significa que el archivo no se implementa con la solución. Tendrá que establecer otro valor para la propiedad a fin de incluir el archivo en el paquete.

 Por ejemplo, para agregar un archivo *.xml* a un proyecto de SharePoint, realice una de estas acciones:

- Agregue una carpeta asignada "Layouts" (Diseños) de SharePoint al proyecto. Esto crea en el **Explorador de soluciones** una carpeta denominada **Layouts** con una subcarpeta para el proyecto. Agregue el archivo *.xml* a la nueva subcarpeta. De forma predeterminada, el archivo se implementa en el sistema de archivos de SharePoint en *..\TEMPLATE\LAYOUTS\\\<Folder Name>* . Para obtener más información sobre cómo agregar carpetas asignadas, vea [Procedimiento para agregar y quitar carpetas asignadas](../sharepoint/how-to-add-and-remove-mapped-folders.md).

- Agregue el archivo *.xml* a la carpeta de un elemento de proyecto de SharePoint y, después, cambie la propiedad **Tipo de implementación** del archivo *.xml* de **NoDeployment** a otra opción como **RootFile** o **ElementFile**. El valor adecuado de **Tipo de implementación** depende del archivo y del proyecto. Para obtener más información sobre los valores de la propiedad **Tipo de implementación**, vea [Desarrollo de soluciones de SharePoint](../sharepoint/developing-sharepoint-solutions.md).

  Si un archivo agregado no se aplica a ningún proyecto específico de la solución, puede agregar un proyecto de SharePoint vacío a la solución y, después, agregarle los archivos adicionales. Otra alternativa para implementar archivos en SharePoint, especialmente en la base de datos de contenido, consiste en agregar un módulo al proyecto y, después, agregar los archivos al módulo. Para obtener más información, vea [Uso de módulos para incluir archivos en la solución](../sharepoint/using-modules-to-include-files-in-the-solution.md).

## <a name="see-also"></a>Consulte también
- [Desarrollar soluciones de SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Build and debug SharePoint solutions](../sharepoint/building-and-debugging-sharepoint-solutions.md) (Compilar y depurar las soluciones de SharePoint)
