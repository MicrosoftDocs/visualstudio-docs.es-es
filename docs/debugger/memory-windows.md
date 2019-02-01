---
title: Ver la memoria para las variables en el depurador | Microsoft Docs
ms.custom: H1Hack27Feb2017
ms.date: 10/04/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.memory
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Memory window
- strings [Visual Studio], viewing
- debugger [Visual Studio], Memory window
- memory [Visual Studio], debugging
- debugging [Visual Studio], Memory window
- buffers, viewing
ms.assetid: 7f7a0439-10e4-4966-bb2d-51f04cda4fe2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 85cbe463d2790a706570dcc53dce44bd825cba13
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55013722"
---
# <a name="use-the-memory-windows-in-the-visual-studio-debugger-c-c-visual-basic-f"></a>Usar las ventanas de memoria en el depurador de Visual Studio (C#, C++, Visual Basic, F#)

Durante la depuración, la **memoria** ventana muestra el espacio de memoria que está usando la aplicación. 

Depurador de windows como **inspección**, **automático**, **variables locales**y el **Inspección rápida** cuadro de diálogo se muestran las variables, que se almacenan en específico ubicaciones de la memoria. El **memoria** ventana muestra la imagen global. La vista de la memoria es conveniente para examinar grandes conjuntos de datos (búferes o cadenas largas, por ejemplo) que no se muestran adecuadamente en las otras ventanas. 

El **memoria** ventana no se limita a mostrar los datos. Muestra todos los elementos en el espacio de memoria, incluidos los datos, código y bits aleatorios de memoria no asignada.  

El **memoria** ventana no está disponible para la depuración de SQL o la secuencia de comandos. Estos lenguajes no reconocen el concepto de memoria.  
  
## <a name="open-a-memory-window"></a>Abra una ventana memoria  
  
Al igual que otras ventanas del depurador, el **memoria** windows están disponibles únicamente durante una sesión de depuración. 

>[!IMPORTANT]
>Para habilitar el **memoria** windows, **habilitar la depuración de nivel de dirección** debe seleccionarse en **herramientas** > **opciones** (o **Depurar** > **opciones**) > **depuración** > **General**. 

**Para abrir una ventana Memoria**
  
1. Asegúrese de que **habilitar la depuración de nivel de dirección** está seleccionado en **herramientas** > **opciones** (o **depurar**  >  **Opciones**) > **depuración** > **General**. 
   
1. Iniciar la depuración seleccionando la flecha verde, al presionar **F5**, o seleccionar **depurar** > **Iniciar depuración**.  
   
2. En **depurar** > **Windows** > **memoria**, seleccione **memoria 1**, **memoria 2**, **Memoria 3**, o **memoria 4**. (Algunas ediciones de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ofrecen sólo uno **memoria** ventana.)  

## <a name="move-around-in-the-memory-window"></a>Mover en la ventana memoria  

El espacio de direcciones de un equipo es grande y fácilmente pueden perder su lugar desplazándose por la **memoria** ventana. 

Las direcciones de memoria más altas aparecen en la parte inferior de la ventana. Para ver una dirección alta, desplácese hacia abajo. Para ver una dirección inferior, desplácese hacia arriba.  

Puede ir al instante a una dirección especificada en el **memoria** ventana mediante arrastrar y colocar, o bien escribiendo la dirección en la **dirección** campo. El **dirección** campo acepta direcciones alfanuméricos y expresiones que se evalúan como direcciones, como `e.User.NonroamableId`. 

Para forzar la reevaluación inmediata de una expresión en el **dirección** , seleccione la flecha redondea **volver a evaluar automáticamente** icono. 

De forma predeterminada, el **memoria** ventana trata **dirección** expresiones como expresiones en directo, que se vuelve a evaluadas cuando se ejecuta la aplicación. Las expresiones en directo pueden ser útiles, por ejemplo, para ver la memoria que se toca por una variable de puntero.  

**Para usar arrastrar y colocar para mover a una ubicación de memoria:**  
   
1. En cualquier ventana de depurador, seleccione una dirección de memoria o una variable de puntero que contiene una dirección de memoria.  
   
2. Arrastre y coloque la dirección o el puntero en el **memoria** ventana. Esa dirección aparece a continuación, en el **dirección** campo y el **memoria** ventana se ajusta para mostrar dicha dirección en la parte superior. 
  
**Para mover a una ubicación de memoria, escríbala en el campo de dirección:**
  
- Escriba o pegue la dirección o una expresión en el **dirección** campo y presione **ENTRAR**, o elíjalo en la lista desplegable en el **dirección** campo. El **memoria** ventana se ajusta para mostrar dicha dirección en la parte superior.
  
## <a name="customize-the-memory-window"></a>Personalizar la ventana memoria 

De forma predeterminada, contenido de la memoria se muestran como enteros de 1 bytes en formato hexadecimal y ancho de la ventana determina el número de columnas que se muestran. Puede personalizar el modo en que la ventana **Memoria** muestra el contenido de la memoria.  
  
**Para cambiar el formato del contenido de la memoria:**  
  
-  Haga clic en el **memoria** ventana y elija los formatos que desee en el menú contextual.  
  
**Para cambiar el número de columnas de la ventana Memoria:**
  
- Seleccione la flecha desplegable junto a la **columnas** campo y seleccione el número de columnas para mostrar, o seleccione **automática** para ajuste automático según el ancho de la ventana.  
  
Si no desea que el contenido de la **memoria** ventana para cambiar a medida que la aplicación se ejecuta, puede desactivar la evaluación de expresiones en directo. 

**Para activar o desactivar la evaluación en directo:**  
  
- Haga clic en el **memoria** ventana y seleccione **volver a evaluar automáticamente** en el menú contextual. 

  >[!NOTE]
  >Expresión de Live es un botón de alternancia evaluación y está activada de forma predeterminada, así que seleccione **volver a evaluar automáticamente** lo desactiva. Seleccionar **volver a evaluar automáticamente** nuevo enciende. 
  
Se puede ocultar o mostrar la barra de herramientas en la parte superior de la ventana **Memoria**. No tendrá acceso a la **dirección** campo u otras herramientas cuando se oculta la barra de herramientas.  
  
**Para alternar la presentación de la barra de herramientas:**  
  
- Haga clic en el **memoria** ventana y seleccione **Mostrar barra de herramientas** en el menú contextual. La barra de herramientas aparece o desaparece según su estado anterior.  
  
## <a name="follow-a-pointer-through-memory"></a>Seguir un puntero a través de la memoria  

En las aplicaciones de código nativo, puede usar nombres de registro como expresiones en directo. Por ejemplo, puede utilizar el puntero de la pila para realizar un seguimiento de la pila.  
  
**Para seguir un puntero a través de la memoria:**
  
1. En el **memoria** ventana **dirección** , escriba una expresión de puntero que se encuentra en el ámbito actual. Dependiendo del lenguaje que utilice, quizá tenga que desreferenciar esta variable.  
  
2. Presione **ENTRAR**.  
   
   Cuando usa un comando de depuración como **paso**, la dirección de memoria mostrada en el **dirección** campo y en la parte superior de la **memoria** ventana cambia automáticamente cuando el puntero cambios.  
  
## <a name="see-also"></a>Vea también  
 [Visualización de datos en el depurador](../debugger/viewing-data-in-the-debugger.md)