---
title: Crear paquetes de soluciones de SharePoint | Documentos de Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
- packages [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e67073d1a12a9412b153adc0c06471c4d39ff15a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="creating-sharepoint-solution-packages"></a>Crear paquetes de soluciones de SharePoint
  Con el Diseñador de paquetes, puede crear y personalizar paquetes de implementación. Por ejemplo, puede agregar elementos y características de proyecto de SharePoint, restablecer el servidor IIS, establecer los ámbitos de activación de las características e identificar las dependencias de las características. El diseñador también genera un manifiesto, un archivo XML en el que se describe cada paquete.  
  
## <a name="packaging-tools"></a>Herramientas para paquetes  
 Puede usar el **Diseñador de paquetes** para personalizar el paquete y generar el manifiesto. Puede incluir elementos de proyecto de SharePoint, configurar si se debería restablecer el servidor web y establecer el tipo de servidor de implementación. Para obtener más información, consulte [Cómo: agregar y quitar características y elementos de un paquete mediante el Diseñador de paquetes](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md).  
  
 Como alternativa, puede usar el **Explorador de empaquetado** para modificar las características y los elementos del archivo empaquetado (.wsp). Para obtener más información, consulte [Cómo: agregar y quitar características y elementos de un paquete mediante el Explorador de empaquetado](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md).  
  
 Puede utilizar Visual Studio y MSBuild para crear los archivos empaquetados (.wsp) para implementar la solución de SharePoint. Este proceso genera los archivos de manifiesto necesarios para la implementación de SharePoint. Para obtener más información, consulte [Cómo: crear un paquete de SharePoint](http://msdn.microsoft.com/en-us/b24be45c-e91d-49bb-afb0-7b265404214b) y [Cómo: crear un paquete de solución de SharePoint mediante tareas de MSBuild](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md).  
  
## <a name="package-designer-options"></a>Opciones del Diseñador de paquetes  
 La siguiente tabla muestra las propiedades que pueden personalizar en los paquetes de SharePoint con el **Diseñador de paquetes**.  
  
|Propiedad del Diseñador de paquetes|Descripción del valor predeterminado|  
|-------------------------------|------------------------------------|  
|nombre|Requerido. El nombre predeterminado del paquete se establece en *ProjectName*.|  
|Restablecer WebServer|Opcional. Seleccione si desea reiniciar el servidor web una vez instalado el archivo .wsp en el servidor de SharePoint.|  
|Tipo de servidor de implementación|Requerido. De forma predeterminada, el ámbito se establece en ApplicationServer.<br /><br /> ApplicationServer: Describe un servidor que hospeda servicios.<br /><br /> WebFrontEnd: Describe un servidor que hospeda sitios Web.|  
|Elementos de la solución|Todos los elementos y las características de proyecto de SharePoint que se pueden agregar al paquete.|  
|Elementos del paquete|Opcional. Todos los elementos y características de SharePoint que desea implementar en su paquete.|  
  
## <a name="configuring-the-packaging-process"></a>Configurar el proceso de empaquetado  
 Después de desarrollar soluciones de SharePoint en Visual Studio, puede personalizar cómo se empaquetan los proyectos.  
  
 En la tabla siguiente se muestran los dos destinos de MSBuild que puede usar para personalizar el modo en que se crea el archivo .wsp.  
  
|Destino|Descripción|  
|------------|-----------------|  
|BeforeLayout|El destino que realiza las tareas inmediatamente antes de que los archivos se copien en un directorio intermedio. Puede modificar los archivos antes de crear un archivo empaquetado (.wsp).|  
|AfterLayout|El destino que realiza las tareas inmediatamente después de que los archivos se copien en un directorio intermedio.|  
  
 Para obtener más información, [Cómo: personalizar un paquete de solución de SharePoint mediante el uso de destinos de MSBuild](../sharepoint/how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets.md).  
  
## <a name="packaging-architecture"></a>Arquitectura de empaquetado  
 A continuación se describen los pasos necesarios para crear un paquete de SharePoint (.wsp) en Visual Studio.  
  
1.  Los paquetes y las características se validan para asegurarse de que la estructura física y semántica del paquete es correcta.  
  
2.  Se enumeran las características, los elementos del proyecto y los archivos empaquetados del paquete. Los archivos de manifiesto para los paquetes y las características se transforman para incluir toda la información necesaria para la implementación y la activación. Los tokens se reemplazan con el valor completo.  
  
3.  Se lleva a cabo el destino BeforeLayout MSBuild. Puede crear este paso para llevar a cabo modificaciones personalizadas en el paquete antes de que se cree el archivo .wsp.  
  
4.  Los archivos enumerados se copian en un directorio intermedio.  
  
5.  Se lleva a cabo el destino AfterLayout MSBuild personalizable. Puede crear este paso para llevar a cabo modificaciones personalizadas en el paquete antes de que se cree el archivo .wsp.  
  
6.  Los archivos del directorio intermedio se agregan al archivo .wsp.  
  
## <a name="package-folder-structure"></a>Estructura de carpetas de los paquetes  
 Si empaqueta un proyecto de SharePoint, se crea un archivo .wsp automáticamente en el SolutionFolder\bin\\*BuildConfiguration* carpeta. Por ejemplo, si la solución está en *unidad*: \Visual Studio 2013\Projects\ListDefinition1 y la configuración de compilación está establecida en liberar, el archivo .wsp se encuentra en *unidad*: \Visual Studio 2013\ Projects\ListDefinition1\bin\Release.  
  
## <a name="see-also"></a>Vea también  
 [Cómo: Personalizar un paquete de solución de SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)  
 [Cómo: agregar y quitar características y elementos de un paquete mediante el Diseñador de paquetes](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)   
 [Cómo: crear un paquete de SharePoint](http://msdn.microsoft.com/en-us/b24be45c-e91d-49bb-afb0-7b265404214b)   
 [Cómo: crear un paquete de solución de SharePoint con las tareas de MSBuild](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md)   
 [Cómo: Personalizar un paquete de solución de SharePoint mediante destinos de MSBuild](../sharepoint/how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets.md)  
  
  