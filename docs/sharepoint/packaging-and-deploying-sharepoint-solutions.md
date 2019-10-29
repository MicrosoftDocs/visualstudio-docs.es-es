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
ms.openlocfilehash: 45815e03d887f4d22f2559acf741f612cab34c49
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/28/2019
ms.locfileid: "72986203"
---
# <a name="package-and-deploy-sharepoint-solutions"></a>Empaquetar e implementar soluciones de SharePoint
  Normalmente, una solución de SharePoint se implementa en un servidor de SharePoint mediante el uso de un archivo de paquete de solución (. wsp). Puede usar Visual Studio para organizar los elementos de proyecto de SharePoint en características y crear un paquete para implementar las características de SharePoint.

 En este tema se proporciona la información siguiente:

- [Crear características y paquetes](#create-features-and-packages)

- [Compatibilidad con herramientas de empaquetado y características](#feature-and-packaging-tool-support)

- [Implementar soluciones de SharePoint](#deploy-sharepoint-solutions)

- [Implementar archivos en soluciones de SharePoint](#deploy-files-in-sharepoint-solutions)

## <a name="create-features-and-packages"></a>Crear características y paquetes
 Puede usar Visual Studio para agrupar los elementos de SharePoint relacionados en una *característica*. Por ejemplo, una característica para una definición de lista de contactos puede incluir la instancia de lista y la definición de lista. Puede combinar estos dos elementos en una sola característica con fines de implementación. Para obtener más información sobre las características, vea [bloque de creación: características](/previous-versions/office/developer/sharepoint-2010/ee537350(v=office.14)).

 A continuación, puede crear un paquete de solución de SharePoint ( *. wsp*) para agrupar varias características, definiciones de sitio, ensamblados y otros archivos en un único paquete, que almacena los archivos en un formato que SharePoint necesita para implementar los archivos en el servidor. Para obtener más información, vea [bloque de creación: soluciones](/previous-versions/office/developer/sharepoint-2010/ee537008(v=office.14)).

## <a name="feature-and-packaging-tool-support"></a>Compatibilidad con herramientas de empaquetado y características
 Puede usar las herramientas de desarrollo de SharePoint en Visual Studio para organizar rápidamente los archivos de SharePoint en características y paquetes de soluciones para facilitar la implementación. Puede usar las siguientes herramientas para configurar la característica y el paquete de la solución.

- Diseñador de características y diseñador de paquetes.

- Explorador de empaquetado, una ventana de herramientas.

- Explorador de soluciones.

### <a name="feature-designer-and-package-designer"></a>Diseñador de características y diseñador de paquetes
 Puede crear características, establecer ámbitos y marcar otras características como dependencias mediante el diseñador de características. El diseñador también muestra el archivo XML final que describe cada característica. Para obtener más información, vea [crear características de SharePoint](../sharepoint/creating-sharepoint-features.md).

 Aplique la característica a un sitio web o grupo de sitios web específico estableciendo su *ámbito* en el diseñador de características. Si se activa una característica para un sitio web individual, la característica solo funciona en ese sitio web concreto. Si se activa una característica para una colección de sitios, los elementos de la característica se aplican a toda la colección de sitios. Para obtener más información, vea [ámbito del elemento](/previous-versions/office/developer/sharepoint-2010/ms476615(v=office.14)).

 Si la característica se basa en otras características, puede establecer una *dependencia de activación de características* para marcar las características dependientes antes de que la característica esté disponible. Una dependencia de activación de características comprueba si las características dependientes ya están activadas en ese ámbito. Para obtener más información, vea [dependencias de activación y ámbito](/previous-versions/office/developer/sharepoint-2010/aa543162(v=office.14)).

 En el diseñador de paquetes, puede agrupar los elementos de SharePoint en un único paquete de solución y configurar si se debe restablecer el servidor Web durante la implementación. Para establecer el tipo de servidor de implementación, utilice la ventana **propiedades** . El diseñador también genera el archivo XML que describe el contenido del paquete. Para obtener más información, vea [crear paquetes de soluciones de SharePoint](../sharepoint/creating-sharepoint-solution-packages.md).

 Durante la implementación, se detiene el servicio Internet Information Services (IIS) para copiar los archivos de solución en el servidor de SharePoint. Con el diseñador de paquetes en Visual Studio, puede seleccionar si se debe reiniciar el servidor Web. Para configurar si la solución se implementa en un servidor front-end web o en un servidor de aplicaciones, use la ventana **propiedades** . Para obtener más información, vea [elemento Solution (solución)](/previous-versions/office/developer/sharepoint-2010/ms412929(v=office.14)).

### <a name="packaging-explorer"></a>Explorador de empaquetado
 Para complementar el diseñador de características y el diseñador de paquetes, puede usar el explorador de empaquetado para agrupar los archivos de SharePoint en características y paquetes. Además, puede ver la vista jerárquica del paquete, las características, los elementos de proyecto de SharePoint y los archivos. El explorador de empaquetado es una ventana de herramientas que puede usar para completar las tareas siguientes:

- Abra archivos y elementos de proyecto de SharePoint.

- Arrastrar y colocar elementos de proyecto de SharePoint de una característica a otra.

- Arrastrar y colocar elementos y características de proyecto de SharePoint de un paquete a otro.

- Agregar una nueva característica a un paquete.

- Abra una característica o un diseñador de paquetes.

- Validar características y paquetes.

  Las herramientas de desarrollo de SharePoint en Visual Studio tienen reglas de validación para ayudar a garantizar que el paquete de la solución tiene el formato correcto. Además, las reglas comprueban que el archivo de solución *. wsp* se puede implementar y activar correctamente en un servidor de SharePoint. Para obtener más información sobre el esquema XML de las características, vea [esquemas de características](/previous-versions/office/developer/sharepoint-2010/ms414322(v=office.14)).

  Puede agregar reglas personalizadas de validación de características y paquetes al sistema de proyectos de SharePoint. Para obtener más información, vea [Cómo: crear reglas personalizadas de validación de características y paquetes para soluciones de SharePoint](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).

  Para obtener más información sobre el explorador de empaquetado, consulte [Cómo: agregar y quitar características y elementos de un paquete mediante el explorador de empaquetado](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md).

### <a name="solution-explorer"></a>Explorador de soluciones
 Puede usar Explorador de soluciones para navegar y abrir los archivos del proyecto de SharePoint. Use el menú contextual de Explorador de soluciones para agregar características, receptores de eventos de características y recursos de características. Además, puede abrir los diseñadores de características y los diseñadores de paquetes para configurar las características y los paquetes para la implementación.

## <a name="deploy-sharepoint-solutions"></a>Implementar soluciones de SharePoint
 Después de personalizar las características y el paquete en Visual Studio, puede crear un archivo *. wsp* para implementar en los servidores de SharePoint. Puede usar Visual Studio para depurar y probar el. *WSP* solo en el servidor de SharePoint en el equipo de desarrollo. Para obtener más información sobre cómo implementar las soluciones de SharePoint en un servidor de SharePoint remoto, vea [implementar una solución](/previous-versions/office/developer/sharepoint-2010/aa544500(v=office.14)).

 También puede personalizar los pasos de implementación en el equipo de desarrollo. Para obtener más información, vea [implementar, publicar y actualizar paquetes de soluciones de SharePoint](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md).

## <a name="deploy-files-in-sharepoint-solutions"></a>Implementar archivos en soluciones de SharePoint
 Normalmente, al agregar un elemento de proyecto de SharePoint a la solución de SharePoint, se incluyen todos los archivos necesarios. Los archivos que se pueden compilar (archivos de código) se integran en el ensamblado de salida de la solución. Sin embargo, es posible que también tenga que agregar archivos no compilables, por ejemplo, *. XML*, *. txt*o archivos de recursos, a un proyecto de SharePoint. Estos archivos no se empaquetan automáticamente en la solución. Para asegurarse de que están empaquetadas, agregue los archivos a una carpeta asignada o a un elemento de proyecto de SharePoint.

 Los archivos agregados a las carpetas asignadas se copian automáticamente en el subárbol de SharePoint cuando se implementa la solución. Los archivos agregados a un elemento de proyecto de SharePoint se implementan en la ubicación especificada en la propiedad **Ubicación de implementación** de cada archivo, que se establece parcialmente en función de la propiedad **tipo de implementación** . De forma predeterminada, el valor de la propiedad **tipo de implementación** es **nodeployment**, lo que significa que el archivo no se implementa con la solución. Debe establecer otro valor para la propiedad para incluir el archivo en el paquete.

 Por ejemplo, para agregar un archivo *. XML* a un proyecto de SharePoint, realice una de estas acciones:

- Agregue una carpeta asignada "layouts" de SharePoint al proyecto. Esto crea en **Explorador de soluciones** una carpeta denominada **layouts** que tiene una subcarpeta para el proyecto. Agregue el archivo *. XML* a la nueva subcarpeta. De forma predeterminada, el archivo se implementa en el sistema de archivos de SharePoint en *. \TEMPLATE\LAYOUTS\\\<nombre de carpeta >* . Para obtener información sobre cómo agregar carpetas asignadas, consulte [Cómo: agregar y quitar carpetas asignadas](../sharepoint/how-to-add-and-remove-mapped-folders.md).

- Agregue el archivo *. XML* a la carpeta de un elemento de proyecto de SharePoint y, a continuación, cambie la propiedad **tipo de implementación** del archivo *. XML* de **nodeployment** a otra configuración como **RootFile** o **ElementFile**. La configuración de **tipo de implementación** adecuada depende del archivo y del proyecto. Para obtener más información sobre la configuración de las propiedades de **tipo de implementación** , vea [desarrollar soluciones de SharePoint](../sharepoint/developing-sharepoint-solutions.md).

  Si un archivo agregado no se aplica a ningún proyecto específico de la solución, puede Agregar un proyecto de SharePoint vacío a la solución y, a continuación, agregarle los archivos adicionales. Otra alternativa para implementar archivos en SharePoint, especialmente en la base de datos de contenido, es agregar un módulo al proyecto y, a continuación, agregar los archivos al módulo. Para obtener más información, vea [usar módulos para incluir archivos en la solución](../sharepoint/using-modules-to-include-files-in-the-solution.md).

## <a name="see-also"></a>Vea también
- [Desarrollar soluciones de SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Build and debug SharePoint solutions](../sharepoint/building-and-debugging-sharepoint-solutions.md) (Compilar y depurar las soluciones de SharePoint)
