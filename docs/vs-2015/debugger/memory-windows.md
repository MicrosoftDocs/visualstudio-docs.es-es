---
title: Ventanas de memoria | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e60f9b3c9acf1377139fee27486bb10251d8804a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68158465"
---
# <a name="memory-windows"></a>Memoria (Ventana)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La ventana **memoria** proporciona una vista en el espacio de memoria que usa la aplicación. La ventana **inspección** , el cuadro de diálogo Inspección **rápida** , la ventana **automático** y la ventana **variables locales** muestran el contenido de las variables, que se almacenan en ubicaciones específicas de la memoria. Pero la ventana **memoria** muestra la imagen a gran escala. Esta visión puede ser conveniente para examinar grandes conjuntos de datos (búferes de cadenas largas, por ejemplo), que no se muestran adecuadamente en las demás ventanas. Sin embargo, la ventana **memoria** no se limita a Mostrar datos. Muestra todo lo que hay en el espacio de memoria, ya sean datos, código o bits aleatorios de la memoria no asignada.  
  
 La ventana **memoria** solo está disponible si está habilitada la depuración de nivel de dirección en el cuadro de diálogo **Opciones** , nodo**depuración** . La ventana **memoria** no está disponible para script o SQL, que son lenguajes que no reconocen el concepto de memoria.  
  
## <a name="opening-a-memory-window"></a>Abrir una ventana Memoria  
  
#### <a name="to-open-a-memory-window"></a>Para abrir una ventana Memoria  
  
1. Inicie la depuración, si aún no está en modo de depuración.  
  
2. En el menú **depurar** , seleccione **ventanas**. A continuación, seleccione **memoria** y, a continuación, haga clic en **memoria 1**, **memoria 2**, **memoria 3**o **memoria 4**. (Las ediciones de nivel inferior de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] tienen una sola ventana de **memoria** . Si usa una de esas ediciones, simplemente haga clic en **memoria**).  
  
## <a name="paging-in-the-memory-window"></a>Paginación en la ventana Memoria  
 La ventana **memoria** tiene una barra de desplazamiento vertical que funciona de forma no estándar. El espacio de direcciones de un equipo moderno es muy grande, por lo que podría perderse fácilmente al arrastrar el control de desplazamiento a una ubicación aleatoria. Por ese motivo, el control de desplazamiento se comporta como un resorte y siempre permanece en el centro de la barra de desplazamiento. En las aplicaciones en código nativo, puede retroceder o avanzar una página, pero no puede desplazarse libremente por la ventana.  
  
 Las direcciones de memoria más altas aparecen en la parte inferior de la ventana. Para ver una dirección más alta, desplácese hacia abajo, no hacia arriba.  
  
#### <a name="to-page-up-or-down-in-memory"></a>Para retroceder o avanzar en la memoria  
  
1. Para avanzar (moverse a una dirección de memoria más alta), haga clic debajo del control de la barra de desplazamiento vertical.  
  
2. Para retroceder (moverse a una dirección de memoria más baja), haga clic encima del control de la barra de desplazamiento vertical.  
  
## <a name="selecting-a-memory-location"></a>Seleccionar una ubicación de memoria  
 Si desea moverse de forma instantánea a una ubicación seleccionada en la memoria, puede hacerlo mediante una operación de arrastrar y colocar, o bien editando el valor en el cuadro **Dirección** . El cuadro **Dirección** acepta no solo valores numéricos sino también expresiones que se evalúan como direcciones. De forma predeterminada, la ventana **memoria** trata una expresión de **Dirección** como una expresión en directo, que se vuelve a evaluar a medida que se ejecuta el programa. Las expresiones en directo pueden ser muy útiles. Puede utilizarlas, por ejemplo, para ver la memoria a la que señala un puntero.  
  
#### <a name="to-select-a-memory-location-by-dragging-and-dropping"></a>Para seleccionar una ubicación de memoria arrastrando y colocando  
  
1. En cualquier ventana, seleccione una dirección de memoria o una variable de puntero que contenga una dirección de memoria.  
  
2. Arrastre la dirección o el puntero a la ventana **memoria** .  
  
#### <a name="to-select-a-memory-location-by-editing"></a>Para seleccionar una ubicación de memoria mediante edición  
  
1. En la ventana **memoria** , seleccione el cuadro **Dirección** .  
  
2. Escriba o pegue la dirección que desea ver y, a continuación, presione **entrar**.  
  
## <a name="changing-the-way-the-memory-window-displays-information"></a>Cambiar la forma en que la ventana Memoria muestra información  
 Puede personalizar el modo en que la ventana **Memoria** muestra el contenido de la memoria. De forma predeterminada, el contenido de la memoria aparece como números enteros en formato hexadecimal, y el número de columnas viene determinado automáticamente por el ancho actual de la ventana.  
  
#### <a name="to-change-the-format-of-the-memory-contents"></a>Para cambiar el formato del contenido de la memoria  
  
1. Haga clic con el botón secundario en la ventana **memoria** .  
  
2. Elija el formato que desee.  
  
#### <a name="to-change-the-number-of-columns-in-the-memory-window"></a>Para cambiar el número de columnas de la ventana Memoria  
  
1. En la barra de herramientas de la parte superior de la ventana **memoria** , busque la lista **columnas** .  
  
2. En la lista **columnas** , seleccione el número de columnas que desea mostrar o seleccione **automático** para el ajuste automático para ajustarse al ancho de la ventana.  
  
   Si no desea que el contenido de la ventana **memoria** cambie a medida que se ejecuta el programa, puede desactivar la evaluación de expresiones en directo.  
  
#### <a name="to-toggle-live-evaluation"></a>Para activar o desactivar la evaluación en directo  
  
1. Haga clic con el botón secundario en la ventana **memoria** .  
  
2. En el menú contextual, haga clic en volver a **evaluar automáticamente**.  
  
    Si la evaluación en directo está habilitada, la opción estará activada y se desactivará al hacer clic en ella. Si la evaluación en directo está deshabilitada, la opción estará desactivada y se activará al hacer clic en ella.  
  
   Se puede ocultar o mostrar la barra de herramientas en la parte superior de la ventana **Memoria**. No tendrá acceso al cuadro Dirección ni a otras herramientas mientras esté oculta la barra de herramientas.  
  
#### <a name="to-toggle-the-toolbar"></a>Para mostrar u ocultar la barra de herramientas  
  
1. Haga clic con el botón secundario en una ventana de **memoria** .  
  
2. En el menú contextual, haga clic en **Mostrar barra de herramientas**.  
  
     La barra de herramientas aparece o desaparece según su estado anterior.  
  
## <a name="following-a-pointer-through-memory"></a>Seguir un puntero a través de la memoria  
 En las aplicaciones de código nativo, puede utilizar nombres de registro como expresiones en directo. Por ejemplo, puede utilizar el puntero de la pila para realizar un seguimiento de la pila.  
  
#### <a name="to-follow-a-pointer-through-memory"></a>Para seguir un puntero a través de la memoria  
  
1. En el cuadro **Dirección** de la ventana **memoria** , escriba una expresión de puntero. La variable de puntero debe encontrarse en el ámbito actual. Dependiendo del lenguaje que utilice, quizá tenga que desreferenciar esta variable.  
  
2. Presione **ENTRAR**.  
  
     Ahora, cuando use un comando de ejecución como **paso**, la dirección de memoria que se muestra cambiará automáticamente a medida que el puntero cambie.  
  
## <a name="see-also"></a>Consulte también  
 [Ver datos en el depurador](../debugger/viewing-data-in-the-debugger.md)
