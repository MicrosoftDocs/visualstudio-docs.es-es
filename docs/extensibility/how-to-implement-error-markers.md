---
title: 'Cómo: implementar marcadores de Error | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - error markers
ms.assetid: e8e78514-5720-4fc2-aa43-00b6af482e38
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f1360f88dba797f96af766f65c9ee41abd6fc808
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31127861"
---
# <a name="how-to-implement-error-markers"></a>Cómo: implementar marcadores de Error
Marcadores de error (o un subrayado ondulado rojo) es los más difíciles de implementar las personalizaciones de editor de texto. Sin embargo, las ventajas que proporcionan a los usuarios de su VSPackage pueden ser mucho mayores que el costo para proporcionarlos. Marcadores de error ligeramente marcan el texto que el analizador de lenguaje considera incorrecto con una línea roja ondulada o línea ondulada de color. Este indicador ayuda a los programadores visualmente mostrando código incorrecto.  
  
 Utilizar marcadores de texto para implementar un subrayado ondulado rojo. Como norma, servicios de lenguaje agregar un subrayado ondulado rojo en el búfer de texto como un paso de segundo plano, ya sea en tiempo de inactividad o en un subproceso en segundo plano.  
  
### <a name="to-implement-the-red-wavy-underline-feature"></a>Para implementar la característica de subrayado ondulado de color rojo  
  
1.  Seleccione el texto en la que desea colocar el subrayado ondulado de color rojo.  
  
2.  Crear un marcador del tipo `MARKER_CODESENSE_ERROR`. Para obtener más información, consulte [Cómo: agregar marcadores de texto estándar](../extensibility/how-to-add-standard-text-markers.md).  
  
3.  A continuación, pase una <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> puntero de interfaz.  
  
 Este proceso también permite crear texto informativo o un menú contextual especial sobre un marcador determinado. Para obtener más información, consulte [Cómo: agregar marcadores de texto estándar](../extensibility/how-to-add-standard-text-markers.md).  
  
 Los objetos siguientes son necesarios para que pueden mostrarse marcadores de error.  
  
-   Un analizador.  
  
-   Un proveedor de tareas (es decir, una implementación de <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2>) que mantiene un registro de cambios en la información de línea con el fin de identificar las líneas para que se puede volver a analizar.  
  
-   Eventos de cambio de un filtro de vista de texto que captura el símbolo de intercalación de la vista utilizando la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEvents.OnChangeCaretLine%2A>) método.  
  
 El analizador, el proveedor de tareas y el filtro proporcionan la infraestructura necesaria para que sea posible marcadores de error. Los pasos siguientes proporcionan el proceso para mostrar marcadores de error.  
  
1.  En la vista que se está filtrando, el filtro Obtiene un puntero al proveedor de tareas asociado con datos de la vista.  
  
    > [!NOTE]
    >  Puede usar el mismo filtro de comando para sugerencias de método, la finalización de instrucciones, los marcadores de error y así sucesivamente.  
  
2.  Cuando el filtro recibe un evento que indica que ha movido a otra línea, se crea una tarea para comprobar si hay errores.  
  
3.  El controlador de tareas comprueba si la línea es defectuoso. Si es así, analiza la línea de errores.  
  
4.  Si se detectan errores, el proveedor de tareas crea una instancia de elemento de tarea. Esta instancia crea el marcador de texto que usa el entorno como un marcador de error en la vista de texto.  
  
## <a name="see-also"></a>Vea también  
 [Uso de marcadores de texto con la API heredado](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Cómo: agregar marcadores de texto estándar](../extensibility/how-to-add-standard-text-markers.md)   
 [Cómo: crear marcadores de texto personalizado](../extensibility/how-to-create-custom-text-markers.md)   
 [Cómo: utilizar marcadores de texto](../extensibility/how-to-use-text-markers.md)