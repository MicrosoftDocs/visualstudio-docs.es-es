---
title: "Memoria (Ventana) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.memory"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Ventana Memoria"
  - "cadenas [Visual Studio], visualización"
  - "depurador [Visual Studio], ventana Memoria"
  - "memoria [Visual Studio], depuración"
  - "depuración [Visual Studio], ventana Memoria"
  - "búferes, visualización"
ms.assetid: 7f7a0439-10e4-4966-bb2d-51f04cda4fe2
caps.latest.revision: 32
caps.handback.revision: 32
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Memoria (Ventana)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La ventana **Memoria** permite ver el espacio de memoria que utiliza la aplicación.  La ventana **Inspección**, el cuadro de diálogo **Inspección rápida**, la ventana **Automático** y la ventana **Variables locales** muestran el contenido de las variables, que se almacenan en ubicaciones específicas de la memoria.  Pero la ventana **Memoria** muestra la imagen a gran escala.  Esta visión puede ser conveniente para examinar grandes conjuntos de datos \(búferes de cadenas largas, por ejemplo\), que no se muestran adecuadamente en las demás ventanas.  Sin embargo, la ventana **Memoria** no se limita a mostrar datos.  Muestra todo lo que hay en el espacio de memoria, ya sean datos, código o bits aleatorios de la memoria no asignada.  
  
 La ventana **Memoria** solo está disponible si la depuración de nivel de dirección está habilitada en el cuadro de diálogo **Opciones**, y el nodo **Depuración**.  La ventana **Memoria** no está disponible para script ni SQL, ya que estos lenguajes no reconocen el concepto de memoria.  
  
## Abrir una ventana Memoria  
  
#### Para abrir una ventana Memoria  
  
1.  Inicie la depuración, si aún no está en modo de depuración.  
  
2.  En el menú **Depurar**, elija **Ventanas**.  A continuación, elija **Memoria** y, a continuación, haga clic en **Memoria 1**, **Memoria 2**, **Memoria 3** o **Memoria 4**. \(Las ediciones de nivel inferior de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] tienen una sola ventana **Memoria**.  Si utiliza una de esas ediciones, simplemente haga clic en **Memoria**\).  
  
## Paginación en la ventana Memoria  
 La ventana **Memoria** tiene una barra de desplazamiento vertical que funciona de forma no estándar.  El espacio de direcciones de un equipo moderno es muy grande, por lo que podría perderse fácilmente al arrastrar el control de desplazamiento a una ubicación aleatoria.  Por ese motivo, el control de desplazamiento se comporta como un resorte y siempre permanece en el centro de la barra de desplazamiento.  En las aplicaciones en código nativo, puede retroceder o avanzar una página, pero no puede desplazarse libremente por la ventana.  
  
 Las direcciones de memoria más altas aparecen en la parte inferior de la ventana.  Para ver una dirección más alta, desplácese hacia abajo, no hacia arriba.  
  
#### Para retroceder o avanzar en la memoria  
  
1.  Para avanzar \(moverse a una dirección de memoria más alta\), haga clic debajo del control de la barra de desplazamiento vertical.  
  
2.  Para retroceder \(moverse a una dirección de memoria más baja\), haga clic encima del control de la barra de desplazamiento vertical.  
  
## Seleccionar una ubicación de memoria  
 Si desea moverse instantáneamente a una ubicación de memoria seleccionada, utilice la función de arrastrar y colocar o modifique el valor del cuadro **Dirección**.  El cuadro **Dirección** no solo acepta valores numéricos sino también expresiones que se evalúan como direcciones.  De forma predeterminada, la ventana **Memoria** trata una expresión de **Dirección** como una expresión en directo, que se vuelve a evaluar durante la ejecución del programa.  Las expresiones en directo pueden ser muy útiles.  Puede utilizarlas, por ejemplo, para ver la memoria a la que señala un puntero.  
  
#### Para seleccionar una ubicación de memoria arrastrando y colocando  
  
1.  En cualquier ventana, seleccione una dirección de memoria o una variable de puntero que contenga una dirección de memoria.  
  
2.  Arrastre la dirección o el puntero hacia la ventana **Memoria**.  
  
#### Para seleccionar una ubicación de memoria mediante edición  
  
1.  En la ventana **Memoria**, seleccione el cuadro **Dirección**.  
  
2.  Escriba o pegue la dirección que desee ver y, a continuación, presione **ENTRAR**.  
  
## Cambiar la forma en que la ventana Memoria muestra información  
 Puede personalizar el modo en que la ventana **Memoria** muestra el contenido de la memoria.  De forma predeterminada, el contenido de la memoria aparece como números enteros en formato hexadecimal, y el número de columnas viene determinado automáticamente por el ancho actual de la ventana.  
  
#### Para cambiar el formato del contenido de la memoria  
  
1.  Haga clic con el botón secundario del mouse en la ventana **Memoria**.  
  
2.  Elija el formato que desee.  
  
#### Para cambiar el número de columnas de la ventana Memoria  
  
1.  En la barra de herramientas de la parte superior de la ventana **Memoria**, busque la lista **Columnas**.  
  
2.  En la lista **Columnas**, seleccione el número de columnas que desee mostrar o elija **Automático** para que el ajuste se realice automáticamente de acuerdo con el ancho de la ventana.  
  
 Si no desea que el contenido de la ventana **Memoria** cambie conforme se ejecuta el programa, puede desactivar la evaluación de las expresiones en directo.  
  
#### Para activar o desactivar la evaluación en directo  
  
1.  Haga clic con el botón secundario del mouse en la ventana **Memoria**.  
  
2.  En el menú contextual, haga clic en **Volver a evaluar automáticamente**.  
  
     Si la evaluación en directo está habilitada, la opción estará activada y se desactivará al hacer clic en ella.  Si la evaluación en directo está deshabilitada, la opción estará desactivada y se activará al hacer clic en ella.  
  
 Se puede ocultar o mostrar la barra de herramientas en la parte superior de la ventana **Memoria**.  No tendrá acceso al cuadro Dirección ni a otras herramientas mientras esté oculta la barra de herramientas.  
  
#### Para mostrar u ocultar la barra de herramientas  
  
1.  Haga clic con el botón secundario del mouse en la ventana **Memoria**.  
  
2.  En el menú contextual, haga clic en **Mostrar barra de herramientas**.  
  
     La barra de herramientas aparece o desaparece según su estado anterior.  
  
## Seguir un puntero a través de la memoria  
 En las aplicaciones de código nativo, puede utilizar nombres de registro como expresiones en directo.  Por ejemplo, puede utilizar el puntero de la pila para realizar un seguimiento de la pila.  
  
#### Para seguir un puntero a través de la memoria  
  
1.  En el cuadro **Dirección** de la ventana **Memoria**, escriba una expresión de puntero.  La variable de puntero debe encontrarse en el ámbito actual.  Dependiendo del lenguaje que utilice, quizá tenga que desreferenciar esta variable.  
  
2.  Presione **ENTRAR**.  
  
     Ahora, cuando utilice un comando de ejecución como **Step**, la dirección de memoria que se muestra cambiará automáticamente conforme cambie el puntero.  
  
## Vea también  
 [Ver datos en el depurador](../debugger/viewing-data-in-the-debugger.md)