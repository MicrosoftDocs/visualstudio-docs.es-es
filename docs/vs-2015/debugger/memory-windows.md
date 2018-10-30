---
title: Memoria Windows | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.memory
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- Memory window
- strings [Visual Studio], viewing
- debugger [Visual Studio], Memory window
- memory [Visual Studio], debugging
- debugging [Visual Studio], Memory window
- buffers, viewing
ms.assetid: 7f7a0439-10e4-4966-bb2d-51f04cda4fe2
caps.latest.revision: 37
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 140d3e0fb721c9913de6feb6f1ed9249c8b75cfa
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/29/2018
ms.locfileid: "50219528"
---
# <a name="memory-windows"></a>Memoria (Ventana)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El **memoria** ventana proporciona una vista en el espacio de memoria que se usa la aplicación. El **inspección** ventana, **Inspección rápida** cuadro de diálogo, **automático** ventana, y **variables locales** ventana muestran el contenido de las variables, que son se almacenan en ubicaciones específicas en la memoria. Pero la **memoria** ventana muestra la imagen a gran escala. Esta visión puede ser conveniente para examinar grandes conjuntos de datos (búferes de cadenas largas, por ejemplo), que no se muestran adecuadamente en las demás ventanas. Sin embargo, el **memoria** ventana no se limita a mostrar los datos. Muestra todo lo que hay en el espacio de memoria, ya sean datos, código o bits aleatorios de la memoria no asignada.  
  
 El **memoria** ventana solo está disponible si la depuración de nivel de dirección está habilitada en el **opciones** cuadro de diálogo,**depuración** nodo. El **memoria** ventana no está disponible para Script ni SQL, ya que estos lenguajes no reconocen el concepto de memoria.  
  
## <a name="opening-a-memory-window"></a>Abrir una ventana Memoria  
  
#### <a name="to-open-a-memory-window"></a>Para abrir una ventana Memoria  
  
1.  Inicie la depuración, si aún no está en modo de depuración.  
  
2.  En el **depurar** menú, elija **Windows**. A continuación, elija **memoria** y, a continuación, haga clic en **memoria 1**, **memoria 2**, **memoria 3**, o **memoria 4**. (Las ediciones de bajo nivel [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] tienen una sola **memoria** ventana. Si usa una de esas ediciones, simplemente haga clic en **memoria**.)  
  
## <a name="paging-in-the-memory-window"></a>Paginación en la ventana Memoria  
 El **memoria** ventana tiene una barra de desplazamiento vertical funciona de forma no estándar. El espacio de direcciones de un equipo moderno es muy grande, por lo que podría perderse fácilmente al arrastrar el control de desplazamiento a una ubicación aleatoria. Por ese motivo, el control de desplazamiento se comporta como un resorte y siempre permanece en el centro de la barra de desplazamiento. En las aplicaciones en código nativo, puede retroceder o avanzar una página, pero no puede desplazarse libremente por la ventana.  
  
 Las direcciones de memoria más altas aparecen en la parte inferior de la ventana. Para ver una dirección más alta, desplácese hacia abajo, no hacia arriba.  
  
#### <a name="to-page-up-or-down-in-memory"></a>Para retroceder o avanzar en la memoria  
  
1.  Para avanzar (moverse a una dirección de memoria más alta), haga clic debajo del control de la barra de desplazamiento vertical.  
  
2.  Para retroceder (moverse a una dirección de memoria más baja), haga clic encima del control de la barra de desplazamiento vertical.  
  
## <a name="selecting-a-memory-location"></a>Seleccionar una ubicación de memoria  
 Si desea moverse instantáneamente a una ubicación de memoria seleccionada, puede hacerlo mediante una operación de arrastrar y colocar o modificando el valor de la **dirección** cuadro. El **dirección** cuadro acepta no sólo valores numéricos sino también expresiones que se evalúan como direcciones. De forma predeterminada, el **memoria** ventana trata un **dirección** expresión como una expresión en directo que se reevalúa cuando se ejecuta el programa. Las expresiones en directo pueden ser muy útiles. Puede utilizarlas, por ejemplo, para ver la memoria a la que señala un puntero.  
  
#### <a name="to-select-a-memory-location-by-dragging-and-dropping"></a>Para seleccionar una ubicación de memoria arrastrando y colocando  
  
1.  En cualquier ventana, seleccione una dirección de memoria o una variable de puntero que contenga una dirección de memoria.  
  
2.  Arrastre la dirección o un puntero a la **memoria** ventana.  
  
#### <a name="to-select-a-memory-location-by-editing"></a>Para seleccionar una ubicación de memoria mediante edición  
  
1.  En el **memoria** ventana, seleccione el **dirección** cuadro.  
  
2.  Escriba o pegue la dirección que desea ver y, a continuación, presione **ENTRAR**.  
  
## <a name="changing-the-way-the-memory-window-displays-information"></a>Cambiar la forma en que la ventana Memoria muestra información  
 Puede personalizar la forma en la **memoria** ventana muestra el contenido de la memoria. De forma predeterminada, el contenido de la memoria aparece como números enteros en formato hexadecimal, y el número de columnas viene determinado automáticamente por el ancho actual de la ventana.  
  
#### <a name="to-change-the-format-of-the-memory-contents"></a>Para cambiar el formato del contenido de la memoria  
  
1.  Haga clic en el **memoria** ventana.  
  
2.  Elija el formato que desee.  
  
#### <a name="to-change-the-number-of-columns-in-the-memory-window"></a>Para cambiar el número de columnas de la ventana Memoria  
  
1. En la barra de herramientas en la parte superior de la **memoria** ventana, busque la **columnas** lista.  
  
2. En el **columnas** lista, seleccione el número de columnas que desea mostrar o seleccionar **automática** para ajuste automático ajustar el ancho de la ventana.  
  
   Si no desea que el contenido de la **memoria** ventana Cambiar como el programa se ejecuta, puede desactivar la evaluación de expresiones en directo.  
  
#### <a name="to-toggle-live-evaluation"></a>Para activar o desactivar la evaluación en directo  
  
1. Haga clic en el **memoria** ventana.  
  
2. En el menú contextual, haga clic en **volver a evaluar automáticamente**.  
  
    Si la evaluación en directo está habilitada, la opción estará activada y se desactivará al hacer clic en ella. Si la evaluación en directo está deshabilitada, la opción estará desactivada y se activará al hacer clic en ella.  
  
   Puede ocultar o mostrar la barra de herramientas en la parte superior de la **memoria** ventana. No tendrá acceso al cuadro Dirección ni a otras herramientas mientras esté oculta la barra de herramientas.  
  
#### <a name="to-toggle-the-toolbar"></a>Para mostrar u ocultar la barra de herramientas  
  
1.  Haga clic en un **memoria** ventana.  
  
2.  En el menú contextual, haga clic en **Mostrar barra de herramientas**.  
  
     La barra de herramientas aparece o desaparece según su estado anterior.  
  
## <a name="following-a-pointer-through-memory"></a>Seguir un puntero a través de la memoria  
 En las aplicaciones de código nativo, puede utilizar nombres de registro como expresiones en directo. Por ejemplo, puede utilizar el puntero de la pila para realizar un seguimiento de la pila.  
  
#### <a name="to-follow-a-pointer-through-memory"></a>Para seguir un puntero a través de la memoria  
  
1.  En el **memoria** ventana **dirección** , escriba una expresión de puntero. La variable de puntero debe encontrarse en el ámbito actual. Dependiendo del lenguaje que utilice, quizá tenga que desreferenciar esta variable.  
  
2.  Presione **ENTRAR**.  
  
     Ahora, cuando se usa un comando de ejecución como **paso**, la dirección de memoria que se muestra cambiará automáticamente conforme cambie el puntero.  
  
## <a name="see-also"></a>Vea también  
 [Ver datos en el depurador](../debugger/viewing-data-in-the-debugger.md)





