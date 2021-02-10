---
title: Consulta de la memoria para las variables en el depurador | Microsoft Docs
description: Obtenga información sobre cómo usar las ventanas de memoria durante la depuración para ver el espacio de memoria que usa la aplicación. Otras ventanas muestran variables y dónde residen en la memoria.
ms.custom: SEO-VS-2020
ms.date: 10/04/2018
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ddb7a9f22033c24d4e2e925caec73a86f24e4985
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885188"
---
# <a name="use-the-memory-windows-in-the-visual-studio-debugger-c-c-visual-basic-f"></a>Uso de las ventanas de memoria del depurador de Visual Studio (C#, C++, Visual Basic y F#)

Durante la depuración, la ventana **Memoria** muestra el espacio de memoria que usa la aplicación.

Las ventanas del depurador, como **Inspección**, **Automático**, **Variables locales** y el cuadro de diálogo **Inspección rápida**, muestran variables, que se almacenan en ubicaciones específicas de la memoria. La ventana **Memoria** muestra la imagen general. Esta vista de memoria es conveniente para examinar grandes conjuntos de datos (búferes de cadenas largas, por ejemplo), que no se muestran adecuadamente en las demás ventanas.

La ventana **Memoria** no se limita a mostrar datos. Muestra todo lo que hay en el espacio de memoria, ya sean datos, código o bits aleatorios de la memoria no asignada.

La ventana **Memoria** no está disponible para la depuración de scripts ni de SQL. Esos lenguajes no reconocen el concepto de memoria.

## <a name="open-a-memory-window"></a>Apertura de una ventana Memoria

Al igual que otras ventanas del depurador, las ventanas **Memoria** solo están disponibles durante una sesión de depuración.

>[!IMPORTANT]
>Para habilitar las ventanas **Memoria**, la casilla **Habilitar la depuración de nivel de dirección** debe estar activada en **Herramientas** > **Opciones** (o **Depurar** > **Opciones**) > **Depuración** > **General**.

**Para abrir una ventana Memoria**

1. Asegúrese de que la casilla **Habilitar la depuración de nivel de dirección** esté activada en **Herramientas** > **Opciones** (o **Depurar** > **Opciones**) > **Depuración** > **General**.

1. Para iniciar la depuración, seleccione la flecha verde, presione **F5** o seleccione **Depurar** > **Iniciar depuración**.

2. En **Depurar** > **Windows** > **Memoria**, seleccione **Memoria 1**, **Memoria 2**, **Memoria 3** o **Memoria 4**. (Algunas ediciones de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ofrecen solo una ventana **Memoria**).

## <a name="move-around-in-the-memory-window"></a>Desplazamiento por la ventana Memoria

El espacio de direcciones de un equipo es grande y puede perder su lugar fácilmente al desplazarse por la ventana **Memoria**.

Las direcciones de memoria más altas aparecen en la parte inferior de la ventana. Para ver una dirección más alta, desplácese hacia abajo. Para ver una dirección más baja, desplácese hacia arriba.

Para ir a una dirección especificada de forma instantánea en la ventana **Memoria**, use arrastrar y colocar, o bien escriba la dirección en el campo **Dirección**. El campo **Dirección** acepta direcciones alfanuméricas y expresiones que se evalúan como direcciones, tales como `e.User.NonroamableId`.

Para forzar la reevaluación inmediata de una expresión en el campo **Dirección**, seleccione el icono de flecha redondeada **Volver a evaluar automáticamente**.

De manera predeterminada, la ventana **Memoria** trata las expresiones de **Dirección** como expresiones dinámicas, que se vuelven a evaluar a medida que se ejecuta la aplicación. Las expresiones dinámicas pueden ser útiles, por ejemplo, para ver la memoria tocada por una variable de puntero.

**Para usar la función de arrastrar y colocar a fin de desplazarse a una ubicación de memoria:**

1. En cualquier ventana de depurador, seleccione una dirección de memoria o una variable de puntero que contenga una dirección de memoria.

2. Arrastre y coloque la dirección o el puntero en la ventana **Memoria**. A continuación, la dirección aparece en el campo **Dirección** y la ventana **Memoria** se ajusta para mostrarla en la parte superior.

**Para ir a una ubicación de memoria escribiéndola en el campo Dirección:**

- Escriba o pegue la dirección o expresión en el campo **Dirección** y presione **Entrar**, o bien elíjala en la lista desplegable del campo **Dirección**. La ventana **Memoria** se ajusta para mostrar esa dirección en la parte superior.

## <a name="customize-the-memory-window"></a>Personalización de la ventana Memoria

De forma predeterminada, el contenido de la memoria aparece como números enteros de 1 byte en formato hexadecimal, y el ancho de la ventana determina el número de columnas que se muestra. Puede personalizar el modo en que la ventana **Memoria** muestra el contenido de la memoria.

**Para cambiar el formato del contenido de la memoria:**

- Haga clic con el botón derecho en la ventana **Memoria** y elija los formatos que quiera en el menú contextual.

**Para cambiar el número de columnas de la ventana Memoria:**

- Seleccione la flecha desplegable situada junto al campo **Columnas** y seleccione el número de columnas que quiera mostrar, o bien seleccione **Automático** para que se ajuste automáticamente en función del ancho de la ventana.

Si no quiere que el contenido de la ventana **Memoria** cambie conforme se ejecute la aplicación, puede desactivar la evaluación de las expresiones dinámicas.

**Para activar o desactivar la evaluación en directo:**

- Haga clic con el botón derecho en la ventana **Memoria** y seleccione **Volver a evaluar automáticamente** en el menú contextual.

  >[!NOTE]
  >La evaluación de expresiones dinámicas es un comando de alternancia y está activada de forma predeterminada, por lo que se desactiva al seleccionar **Volver a evaluar automáticamente**. Al seleccionar **Volver a evaluar automáticamente**, se vuelve a activar.

Se puede ocultar o mostrar la barra de herramientas en la parte superior de la ventana **Memoria**. No tendrá acceso al campo **Dirección** ni a otras herramientas si la barra de herramientas esté oculta.

**Para mostrar u ocultar la barra de herramientas:**

- Haga clic con el botón derecho en la ventana **Memoria** y seleccione **Mostrar barra de herramientas** en el menú contextual. La barra de herramientas aparece o desaparece según su estado anterior.

## <a name="follow-a-pointer-through-memory"></a>Seguimiento de un puntero a través de la memoria

En las aplicaciones de código nativo, puede utilizar nombres de registro como expresiones dinámicas. Por ejemplo, puede utilizar el puntero de la pila para realizar un seguimiento de la pila.

**Para seguir un puntero a través de la memoria:**

1. En el campo **Dirección** de la ventana **Memoria**, escriba una expresión de puntero que esté en el ámbito actual. Dependiendo del lenguaje que utilice, quizá tenga que desreferenciar esta variable.

2. Presione **ENTRAR**.

   Al usar un comando de depuración, como **Depurar paso a paso por instrucciones**, la dirección de memoria que se muestra en el campo **Dirección** y en la parte superior de la ventana **Memoria** cambia automáticamente a medida que también lo hace el puntero.

## <a name="see-also"></a>Vea también
- [Visualización de datos en el depurador](../debugger/viewing-data-in-the-debugger.md)