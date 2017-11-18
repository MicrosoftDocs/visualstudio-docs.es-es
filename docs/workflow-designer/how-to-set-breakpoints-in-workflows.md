---
title: "Cómo: establecer puntos de interrupción en flujos de trabajo | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: e41b21c9-c061-4358-8e2f-eb5e412864a8
caps.latest.revision: "10"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: a5565a5f53506ee61cc40cdd09ab4719bef0742b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-set-breakpoints-in-workflows"></a>Cómo establecer puntos de interrupción en los flujos de trabajo
Al utilizar [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)], puede establecer puntos de interrupción en sus flujos de trabajo gráficos del mismo modo que haría en Visual Basic o en código C#. Como es de esperar, la ejecución del flujo de trabajo se detiene en cada punto de interrupción que se establece.  
  
 Un punto de interrupción tiene tres estados: *pendiente*, *enlazados*, y *Error*. Cuando se establece un punto de interrupción, está En espera y se representa mediante un icono rojo. Cuando el tiempo de ejecución haya cargado el tipo de flujo de trabajo, pasa a Enlazado. Si se especifica un formato incorrecto para el punto de interrupción, como con un nombre de actividad que no es válido, aparece una ventana de error. El punto de interrupción, de todas formas, se agrega a la ventana de punto de interrupción, pero se marca con una "x" pequeña.  
  
> [!NOTE]
>  No se pueden establecer puntos de interrupción en los flujos de trabajo invocados.  
  
> [!WARNING]
>  Asegúrese de seleccionar la opción **habilitar solo mi código (sólo administrado)** desde el **herramientas**, **opciones**, **depuración** menú antes de depurar. Si tiene dos secuencias anidadas en otra secuencia y establecer un punto de interrupción en la primera secuencia interna, si presiona **F11** , no se depurará la segunda secuencia interna si el **habilitar solo mi código (sólo administrado)**opción no está seleccionada.  
  
> [!WARNING]
>  Los puntos de interrupción de un flujo de trabajo no se alcanzarán si la ruta de acceso completa a la propiedad de archivo XAML no es exacta. La ruta de acceso completa al archivo XAML no es exacta después de mover el proyecto o la solución a otra carpeta o a otro equipo. Presione CTRL+S para guardar y actualizar la ruta de acceso completa.  
  
### <a name="to-set-a-breakpoint-on-an-activity-in-the-design-view"></a>Para establecer un punto de interrupción en una actividad en la vista Diseño  
  
1.  Seleccione la actividad donde desee que se interrumpa el depurador.  
  
2.  En el **depurar** menú, seleccione **Alternar puntos de interrupción**. Aparecerá un icono rojo en el borde izquierdo superior de la actividad.  
  
     Como alternativa, también puede presionar el método abreviado **F9** clave después de que puede seleccionar la actividad o se haga clic en la actividad y seleccione **punto de interrupción** , a continuación, **Insertar punto de interrupción**en el menú contextual.  
  
## <a name="see-also"></a>Vea también  
 [Cómo: invocar el depurador de flujo de trabajo](../workflow-designer/how-to-invoke-the-workflow-debugger.md)   
 [Depurar flujos de trabajo con el Diseñador de flujo de trabajo](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)   
 [Cómo: Depurar XAML con el Diseñador de flujo de trabajo](../workflow-designer/how-to-debug-xaml-with-the-workflow-designer.md)