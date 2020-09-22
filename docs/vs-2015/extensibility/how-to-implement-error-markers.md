---
title: 'Cómo: implementar marcadores de error | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - error markers
ms.assetid: e8e78514-5720-4fc2-aa43-00b6af482e38
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2af9e0765fb5bc73a35bebfc2f50f5d2a41122d3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842710"
---
# <a name="how-to-implement-error-markers"></a>Cómo: Implementar marcadores de error
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Los marcadores de error (o el subrayado ondulado rojo) son las más difíciles de implementar en las personalizaciones del editor de texto. Sin embargo, las ventajas que ofrecen a los usuarios de su VSPackage pueden superar mucho el costo de proporcionarlas. Los marcadores de error marcan sutilmente el texto que el analizador de lenguaje considera incorrecto con una línea roja ondulada o ondulada. Este indicador ayuda a los programadores a mostrar visualmente el código incorrecto.  
  
 Use marcadores de texto para implementar el subrayado ondulado de color rojo. Como norma general, los servicios de lenguaje agregan subrayados ondulados de color rojo al búfer de texto como una fase de fondo, ya sea en tiempo de inactividad o en un subproceso en segundo plano.  
  
### <a name="to-implement-the-red-wavy-underline-feature"></a>Para implementar la característica de subrayado ondulado de color rojo  
  
1. Seleccione el texto en el que desea colocar el subrayado ondulado de color rojo.  
  
2. Cree un marcador del tipo `MARKER_CODESENSE_ERROR` . Para obtener más información, consulte [Cómo: agregar marcadores de texto estándar](../extensibility/how-to-add-standard-text-markers.md).  
  
3. Después, pase un puntero de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interfaz.  
  
   Este proceso también permite crear texto de información sobre herramientas o un menú contextual especial sobre un marcador determinado. Para obtener más información, consulte [Cómo: agregar marcadores de texto estándar](../extensibility/how-to-add-standard-text-markers.md).  
  
   Los siguientes objetos son necesarios antes de que se puedan mostrar los marcadores de error.  
  
- Un analizador.  
  
- Un proveedor de tareas (es decir, una implementación de <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2> ) que mantiene un registro de los cambios en la información de línea con el fin de identificar las líneas que se van a analizar.  
  
- Un filtro de la vista de texto que captura los eventos de cambio del símbolo de intercalación de la vista mediante el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEvents.OnChangeCaretLine%2A> método).  
  
  El analizador, el proveedor de tareas y el filtro proporcionan la infraestructura necesaria para hacer posibles marcadores de error. En los pasos siguientes se proporciona el proceso para mostrar marcadores de error.  
  
1. En una vista que se está filtrando, el filtro obtiene un puntero al proveedor de tareas asociado a los datos de esa vista.  
  
    > [!NOTE]
    > Puede usar el mismo filtro de comandos para las sugerencias de métodos, la finalización de instrucciones, los marcadores de error, etc.  
  
2. Cuando el filtro recibe un evento que indica que se ha despasado a otra línea, se crea una tarea para comprobar si hay errores.  
  
3. El controlador de tareas comprueba si la línea está desfasada. Si es así, analiza la línea en busca de errores.  
  
4. Si se detectan errores, el proveedor de tareas crea una instancia de elemento de tarea. Esta instancia crea el marcador de texto que el entorno usa como marcador de error en la vista de texto.  
  
## <a name="see-also"></a>Consulte también  
 [Uso de marcadores de texto con la API heredada](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Cómo: agregar marcadores de texto estándar](../extensibility/how-to-add-standard-text-markers.md)   
 [Cómo: crear marcadores de texto personalizados](../extensibility/how-to-create-custom-text-markers.md)   
 [Cómo: Usar marcadores de texto](../extensibility/how-to-use-text-markers.md)
