---
title: "C&#243;mo: implementar marcadores de Error | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editores [Visual Studio SDK] heredados - marcadores de error"
ms.assetid: e8e78514-5720-4fc2-aa43-00b6af482e38
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# C&#243;mo: implementar marcadores de Error
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Los marcadores del error \(o subrayados ondulados rojos\) son más difíciles de las personalizaciones del editor de texto de implementar.  Sin embargo, las ventajas que proporcionan a los usuarios de VSPackage pueden sobrepasar aparte el costo para así.  Los marcadores de error marcan sutil texto que el analizador de lenguaje juzga incorrecto con un onduladas o una línea roja ondulada.  Este marcador ayuda programadores visualmente mostrar código incorrecto.  
  
 Marcadores de texto de uso para implementar los subrayados ondulados rojos.  En general, los servicios agregan subrayado ondulados rojos al búfer de texto como parte del fondo, en tiempo de inactividad o en un subproceso de fondo.  
  
### Para implementar la característica de subrayado ondulado rojo  
  
1.  Seleccione el texto en el que se desea el lugar el subrayado ondulado rojo.  
  
2.  Cree un marcador de tipo `MARKER_CODESENSE_ERROR`.  Para obtener más información, vea [Cómo: agregar marcadores de texto estándar](../extensibility/how-to-add-standard-text-markers.md).  
  
3.  Después, pase un puntero de interfaz de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> .  
  
 Este proceso también permite crear el texto de sugerencia o un menú contextual especial sobre un marcador especificado.  Para obtener más información, vea [Cómo: agregar marcadores de texto estándar](../extensibility/how-to-add-standard-text-markers.md).  
  
 Se requieren los siguientes objetos antes de que los marcadores de error pueden mostrar.  
  
-   un analizador.  
  
-   Un proveedor de la tarea \(es decir, una implementación de <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2>\) que mantiene un registro de cambios en la información de la línea para identificar las líneas se analizarán.  
  
-   Un filtro de la vista de texto que captura los eventos de cambio del símbolo de intercalación de vista usando el método de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEvents.OnChangeCaretLine%2A>\).  
  
 El analizador, el proveedor de la tarea, y el filtro proporcionan la infraestructura necesaria para hacer marcadores de error posibles.  Los siguientes pasos proporcionan el proceso para mostrar marcadores de error.  
  
1.  En una vista que está filtrando, el filtro obtiene un puntero al proveedor de la tarea asociada con los datos de esa vista.  
  
    > [!NOTE]
    >  Puede usar el mismo filtro para las sugerencias de método, finalización de instrucciones, marcadores del error, etc.  
  
2.  Cuando el filtro recibe un evento que indica que se ha movido a otra línea, se crea una tarea de comprobar si hay errores.  
  
3.  Comprobaciones de controlador de tarea si la línea es modificada.  Si es así analiza la línea de errores.  
  
4.  Si se encuentran errores, el proveedor de la tarea crea una instancia del elemento task.  Esta instancia crea el marcador de texto que el entorno utiliza como marcador de error en la vista de texto.  
  
## Vea también  
 [Uso de marcadores de texto con la API heredada](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Cómo: agregar marcadores de texto estándar](../extensibility/how-to-add-standard-text-markers.md)   
 [Cómo: crear marcadores de texto personalizado](../extensibility/how-to-create-custom-text-markers.md)   
 [Cómo: utilizar marcadores de texto](../extensibility/how-to-use-text-markers.md)