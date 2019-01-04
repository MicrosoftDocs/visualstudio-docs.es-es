---
title: Crear paquetes de soluciones de SharePoint | Microsoft Docs
ms.date: 02/02/2017
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
ms.openlocfilehash: 0d275b7d2e4ccfea5d89148b6b46883fa32e6560
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53966669"
---
# <a name="create-sharepoint-solution-packages"></a>Crear paquetes de solución SharePoint
  Con el Diseñador de paquetes, puede crear y personalizar paquetes de implementación. Por ejemplo, puede agregar elementos y características de proyecto de SharePoint, restablecer el servidor IIS, establecer los ámbitos de activación de las características e identificar las dependencias de las características. El diseñador también genera un manifiesto, un archivo XML en el que se describe cada paquete.  
  
## <a name="packaging-tools"></a>Herramientas de empaquetado
 Puede usar el **Diseñador de paquetes** para personalizar el paquete y generar el manifiesto. Puede incluir elementos de proyecto de SharePoint, configurar si se debería restablecer el servidor web y establecer el tipo de servidor de implementación. Para obtener más información, vea [Cómo: Agregar y quitar características y elementos de un paquete mediante el Diseñador de paquetes](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md).  
  
 Como alternativa, puede usar el **Explorador de empaquetado** para modificar las características y elementos en el archivo de paquete (*.wsp*). Para obtener más información, vea [Cómo: Agregar y quitar características y elementos de un paquete mediante el Explorador de empaquetado](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md).  
  
 Puede usar Visual Studio y MSBuild para crear paquete (*.wsp*) archivos para implementar la solución de SharePoint. Este proceso genera los archivos de manifiesto necesarios para la implementación de SharePoint. Para obtener más información, vea [Cómo: Crear un paquete de solución de SharePoint mediante el uso de las tareas de MSBuild](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md).  
  
## <a name="package-designer-options"></a>Opciones del Diseñador de paquetes
 En la tabla siguiente se muestra las propiedades que se pueden personalizar en los paquetes de SharePoint con el **Diseñador de paquetes**.  
  
|Propiedad del Diseñador de paquetes|Descripción del valor predeterminado|  
|-------------------------------|------------------------------------|  
|nombre|Obligatorio. El nombre predeterminado del paquete se establece en *ProjectName*.|  
|Restablecer WebServer|Opcional. Seleccione si desea reiniciar el servidor Web después de la *.wsp* archivo está instalado en el servidor de SharePoint.|  
|Tipo de servidor de implementación|Obligatorio. De forma predeterminada, el ámbito se establece en ApplicationServer.<br /><br /> ApplicationServer: Describe un servidor que hospeda servicios.<br /><br /> WebFrontEnd: Describe un servidor que hospeda sitios web.|  
|Elementos de la solución|Todos los elementos y las características de proyecto de SharePoint que se pueden agregar al paquete.|  
|Elementos del paquete|Opcional. Todos los elementos y características de SharePoint que desea implementar en su paquete.|  
  
## <a name="configure-the-packaging-process"></a>Configurar el proceso de empaquetado
 Después de desarrollar soluciones de SharePoint en Visual Studio, puede personalizar cómo se empaquetan los proyectos.  
  
 La siguiente tabla muestra los dos destinos de MSBuild que puede usar para personalizar cómo el *.wsp* se crea el archivo.  
  
|Destino|Descripción|  
|------------|-----------------|  
|BeforeLayout|El destino que realiza las tareas inmediatamente antes de que los archivos se copien en un directorio intermedio. Puede modificar los archivos antes de crear un archivo de paquete (*.wsp*).|  
|AfterLayout|El destino que realiza las tareas inmediatamente después de que los archivos se copien en un directorio intermedio.|  
  
 Para obtener más información, [Cómo: Personalizar un paquete de solución de SharePoint mediante destinos de MSBuild](../sharepoint/how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets.md).  
  
## <a name="packaging-architecture"></a>Arquitectura de empaquetado
 Los pasos siguientes se producen cuando se crea un paquete de SharePoint (*.wsp*) en Visual Studio.  
  
1.  Los paquetes y las características se validan para asegurarse de que la estructura física y semántica del paquete es correcta.  
  
2.  Se enumeran las características, los elementos del proyecto y los archivos empaquetados del paquete. Los archivos de manifiesto para los paquetes y las características se transforman para incluir toda la información necesaria para la implementación y la activación. Los tokens se reemplazan con el valor completo.  
  
3.  Se lleva a cabo el destino BeforeLayout MSBuild. Puede crear este paso para realizar modificaciones personalizadas en el paquete antes de la *.wsp* se crea el archivo.  
  
4.  Los archivos enumerados se copian en un directorio intermedio.  
  
5.  Se lleva a cabo el destino AfterLayout MSBuild personalizable. Puede crear este paso para realizar modificaciones personalizadas en el paquete antes de la *.wsp* se crea el archivo.  
  
6.  Los archivos del directorio intermedio se agregan a la *.wsp* archivo.  
  
## <a name="package-folder-structure"></a>Estructura de carpetas de los paquetes
 Al empaquetar el proyecto de SharePoint, un *.wsp* archivo se crea automáticamente en el *SolutionFolder\bin\\\<BuildConfiguration >* carpeta. Por ejemplo, si la solución está en *C:\Visual Studio 2013\proyectos\listdefinition1* y la configuración de compilación se establece en la versión, la *.wsp* archivo se encuentra en *C:\Visual Studio 2013\ Projects\ListDefinition1\bin\Release*.  
  
## <a name="see-also"></a>Vea también
 [Cómo: Personalizar un paquete de solución de SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)  
 [Cómo: Agregar y quitar características y elementos de un paquete mediante el Diseñador de paquetes](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)   
 [Cómo: Crear un paquete de solución de SharePoint mediante el uso de las tareas de MSBuild](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md)   
 [Cómo: Crear un paquete de solución de SharePoint mediante el uso de las tareas de MSBuild](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md)   
 [Cómo: Personalizar un paquete de solución de SharePoint mediante destinos de MSBuild](../sharepoint/how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets.md)  
