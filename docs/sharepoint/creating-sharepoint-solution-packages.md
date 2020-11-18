---
title: Crear paquetes de soluciones de SharePoint | Microsoft Docs
description: Crear y personalizar paquetes de implementación para soluciones de SharePoint mediante el diseñador de paquetes. Explore las herramientas de empaquetado, las opciones del diseñador y la estructura de carpetas.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
- packages [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: bbe458f6ab4de01ffb224ae4e493bf23e3fc6ceb
ms.sourcegitcommit: ad2c820b280b523a7f7aef89742cdb719354748f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/18/2020
ms.locfileid: "94850564"
---
# <a name="create-sharepoint-solution-packages"></a>Crear paquetes de soluciones de SharePoint
  Con el Diseñador de paquetes, puede crear y personalizar paquetes de implementación. Por ejemplo, puede agregar elementos y características de proyecto de SharePoint, restablecer el servidor IIS, establecer los ámbitos de activación de las características e identificar las dependencias de las características. El diseñador también genera un manifiesto, un archivo XML en el que se describe cada paquete.

## <a name="packaging-tools"></a>Herramientas de empaquetado
 Puede usar el **Diseñador de paquetes** para personalizar el paquete y generar el manifiesto. Puede incluir elementos de proyecto de SharePoint, configurar si se debería restablecer el servidor web y establecer el tipo de servidor de implementación. Para obtener más información, vea [Cómo: agregar y quitar características y elementos de un paquete mediante el diseñador de paquetes](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md).

 Como alternativa, puede usar el **Explorador de empaquetado** para modificar las características y los elementos del archivo de paquete (*. wsp*). Para obtener más información, vea [Cómo: agregar y quitar características y elementos de un paquete mediante el explorador de empaquetado](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md).

 Puede usar Visual Studio y MSBuild para crear archivos de paquete (*. wsp*) para implementar la solución de SharePoint. Este proceso genera los archivos de manifiesto necesarios para la implementación de SharePoint. Para obtener más información, vea [Cómo: crear un paquete de solución de SharePoint mediante tareas de MSBuild](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md).

## <a name="package-designer-options"></a>Opciones del diseñador de paquetes
 En la tabla siguiente se muestran las propiedades que se pueden personalizar en los paquetes de SharePoint con el **Diseñador de paquetes**.

|Propiedad del Diseñador de paquetes|Descripción del valor predeterminado|
|-------------------------------|------------------------------------|
|Nombre|Necesario. El nombre predeterminado del paquete se establece en *projectname*.|
|Restablecer WebServer|Opcional. Seleccione esta opciones si desea reiniciar el servidor Web después de instalar el archivo *. wsp* en el servidor de SharePoint.|
|Tipo de servidor de implementación|Opcional. Representa el tipo de servidor que hospeda el paquete. Si no se establece, el valor predeterminado será WebFrontend.<br /><br /> ApplicationServer: describe un servidor que hospeda servicios.<br /><br /> WebFrontend: describe un servidor que hospeda sitios Web.|
|Elementos de la solución|Todos los elementos y las características de proyecto de SharePoint que se pueden agregar al paquete.|
|Elementos del paquete|Opcional. Todos los elementos y características de SharePoint que desea implementar en su paquete.|

## <a name="configure-the-packaging-process"></a>Configurar el proceso de empaquetado
 Después de desarrollar las soluciones de SharePoint en Visual Studio, puede personalizar cómo se empaquetan los proyectos.

 En la tabla siguiente se muestran los dos destinos de MSBuild que puede usar para personalizar cómo se crea el archivo *. wsp* .

|Destino|Descripción|
|------------|-----------------|
|BeforeLayout|El destino que realiza las tareas inmediatamente antes de que los archivos se copien en un directorio intermedio. Puede modificar los archivos antes de crear un archivo de paquete (*. wsp*).|
|AfterLayout|El destino que realiza las tareas inmediatamente después de que los archivos se copien en un directorio intermedio.|

 Para obtener más información, [Cómo: personalizar un paquete de solución de SharePoint mediante destinos de MSBuild](../sharepoint/how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets.md).

## <a name="packaging-architecture"></a>Arquitectura de empaquetado
 Los pasos siguientes se producen al crear un paquete de SharePoint (*. wsp*) en Visual Studio.

1. Los paquetes y las características se validan para asegurarse de que la estructura física y semántica del paquete es correcta.

2. Se enumeran las características, los elementos del proyecto y los archivos empaquetados del paquete. Los archivos de manifiesto para los paquetes y las características se transforman para incluir toda la información necesaria para la implementación y la activación. Los tokens se reemplazan con el valor completo.

3. Se lleva a cabo el destino BeforeLayout MSBuild. Puede crear este paso para realizar modificaciones personalizadas en el paquete antes de que se cree el archivo *. wsp* .

4. Los archivos enumerados se copian en un directorio intermedio.

5. Se lleva a cabo el destino AfterLayout MSBuild personalizable. Puede crear este paso para realizar modificaciones personalizadas en el paquete antes de que se cree el archivo *. wsp* .

6. Los archivos del directorio intermedio se agregan al archivo *. wsp* .

## <a name="package-folder-structure"></a>Estructura de carpetas de los paquetes
 Al empaquetar el proyecto de SharePoint, se crea un archivo *. wsp* en la carpeta *SolutionFolder\bin \\ \<BuildConfiguration>* Por ejemplo, si la solución está en *C:\Visual Studio 2013 \ Projects\ListDefinition1* y la configuración de compilación se establece en release, el archivo *. wsp* se encuentra en *C:\Visual Studio 2013 \ Projects\ListDefinition1\bin\Release*.

## <a name="see-also"></a>Consulte también
- [Cómo: personalizar un paquete de solución de SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)
- [Cómo: agregar y quitar características y elementos de un paquete mediante el diseñador de paquetes](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)
- [Cómo: crear un paquete de solución de SharePoint mediante tareas de MSBuild](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md)
- [Cómo: crear un paquete de solución de SharePoint mediante tareas de MSBuild](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md)
- [Cómo: personalizar un paquete de solución de SharePoint mediante destinos de MSBuild](../sharepoint/how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets.md)
