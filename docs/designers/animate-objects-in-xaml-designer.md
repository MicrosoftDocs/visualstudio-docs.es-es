---
title: "Animar objetos en el Diseñador XAML | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fb88fa26-e835-47f5-9771-2f279441c83c
caps.latest.revision: "9"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1f4fd45337ebd0f00362d352077cf8441e6f5afa
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="animate-objects-in-xaml-designer"></a>Animar objetos en el Diseñador XAML
Cree animaciones cortas para el movimiento y el fundido de objetos.  
  
 Para empezar, cree un *guión gráfico*, que puede contener una o más *escalas de tiempo*. Establezca *fotogramas clave* en una escala de tiempo para marcar los cambios de propiedad. Luego, al ejecutar la animación, Blend interpola los cambios de propiedad durante el período de tiempo designado, lo que produce una transición fluida. Se puede animar cualquier propiedad que pertenezca a un objeto, incluso las propiedades no visuales.  
  
 La siguiente ilustración muestra un guión gráfico denominado **MoveUp**. La escala de tiempo contiene fotogramas clave que marcan la posición X e Y de un rectángulo. Cuando se ejecuta esta animación, el rectángulo se mueve de una posición a otra de manera fluida.  
  
 ![](../designers/media/982f031a-74a3-414a-abc2-a0f41a741075.png "982f031a-74a3-414a-abc2-a0f41a741075")  
  
 Aprenda a crear animaciones con estos vídeos.  
  
|Vea un vídeo corto:|Vea cómo:|  
|--------------------------|-------------------|  
|![Configurar las características instaladas](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Crear escalas de tiempo](http://www.popscreen.com/v/6A4eF/Microsoft-Expression-Blend-Creating-Timelines)|Crear una escala de tiempo y trabajar con objetos en la escala de tiempo.|  
|![Configurar las características instaladas](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Agregar fotogramas clave y repetir la animación](http://www.popscreen.com/v/6A4fi/Microsoft-Expression-Blend-Adding-Keyframes-and-Repeating-an-Animation)|Agregar fotogramas clave y establecer en ellos propiedades. A continuación, ejecutar la animación y ver la transición fluida de los objetos.|  
|![Configurar las características instaladas](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Agregar desencadenadores de eventos de inactividad](http://www.popscreen.com/v/6A4e4/Microsoft-Expression-Blend-Adding-Event-Triggers-for-Interactivity)|Iniciar una animación cuando se produce un evento. Por ejemplo, inicie una cuando se carga la ventana.|  
|![Configurar las características instaladas](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Colores de animación](http://www.popscreen.com/v/6A4gv/Microsoft-Expression-Blend-Animating-Colors)|Usar una animación para cambiar el color de un objeto.|  
|![Configurar las características instaladas](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Crear y modificar trayectorias de animación](http://www.popscreen.com/v/6A4fX/Microsoft-Expression-Blend-Creating-and-Modifying-Motion-Paths)|Animar objetos a lo largo de un trazado.|  
|![Configurar las características instaladas](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Entrada y salida lentas de fotogramas clave](http://www.popscreen.com/v/6A4dM/Microsoft-Expression-Blend-Easing-Keyframes)|Aumentar o reducir la velocidad de una animación cerca del principio (*entrada lenta*) o cerca del final (*salida lenta*) de una animación.|  
|![Configurar las características instaladas](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Animar un botón](http://www.popscreen.com/v/6A4fK/Microsoft-Expression-Blend-Animating-a-Button)|Crear efectos interesantes que aparecen en un botón cuando el usuario apunta a él.|  
|![Configurar las características instaladas](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Crear una animación y trabajar con entradas y salidas lentas](https://www.youtube.com/watch?v=mAJXYrwxGYo)|Animar efectos que aparecen cuando el usuario presiona un botón en la imagen de una calculadora.|  
  
## <a name="see-also"></a>Vea también  
 [Crear una IU con Blend para Visual Studio](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)