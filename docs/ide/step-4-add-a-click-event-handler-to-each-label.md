---
title: "Paso 4: Agregar un controlador de eventos Click a cada etiqueta | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 16bdbc7c-4129-411d-bace-f4a3e5375975
caps.latest.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# Paso 4: Agregar un controlador de eventos Click a cada etiqueta
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El juego de formar parejas funciona como sigue:  
  
1.  Cuando un jugador elige uno de los cuadrados con un icono oculto, el programa le muestra el icono cambiándole el color a negro.  
  
2.  A continuación, el jugador elige otro icono oculto.  
  
3.  Si los iconos coinciden, permanecen visibles.  En caso contrario, se vuelven a ocultar.  
  
 Para conseguir que un programa funcione de esa manera, agregue un controlador de eventos Click que cambie el color de la etiqueta que se elige.  
  
### Para agregar un controlador de eventos Click a cada etiqueta  
  
1.  Abra el formulario en el Diseñador de Windows Forms.  En el Explorador de soluciones, elija Form1.cs o Form1.vb.  En la barra de menús, elija **Ver**, **Diseñador**.  
  
2.  Elija el primer control de etiqueta para seleccionarlo.  A continuación, mantenga presionada la tecla CTRL mientras elige cada una de las otras etiquetas para seleccionarlas.  Asegúrese de que todas las etiquetas están seleccionadas.  
  
3.  Elija el botón **Eventos** en la barra de herramientas de la ventana **Propiedades** para ver la página **Eventos** en la ventana **Propiedades**.  Desplácese hacia abajo hasta el evento **Click** y escriba label\_Click en el cuadro, como se muestra en la siguiente ilustración.  
  
     ![Ventana Propiedades mostrando el evento Click](~/docs/ide/media/express_labelclick.png "Express\_labelClick")  
Ventana Propiedades con el evento Click  
  
4.  Elija la tecla Entrar.  El IDE agrega al código un controlador de eventos Click denominado `label_Click()` y lo enlaza a cada una de las etiquetas del formulario.  
  
5.  Rellene el resto del código como se indica a continuación:  
  
     [!code-cs[VbExpressTutorial4Step2_3_4#4](../ide/codesnippet/CSharp/step-4-add-a-click-event-handler-to-each-label_1.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#4](../ide/codesnippet/VisualBasic/step-4-add-a-click-event-handler-to-each-label_1.vb)]  
  
    > [!NOTE]
    >  Si copia y pega el bloque `label_Click()` de código, en lugar de escribirlo manualmente, asegúrese de reemplazar el código `label_Click()` existente.  De lo contrario, se encontrará con un bloque de código duplicado.  
  
    > [!NOTE]
    >  Tal vez reconozca `object sender` de la parte superior del controlador de eventos como el utilizado en el tutorial [Tutorial 2: Crear una prueba matemática cronometrada](../ide/tutorial-2-create-a-timed-math-quiz.md).  Como enlazó distintos eventos Click de control de etiqueta a un único método de controlador de eventos, se llama al mismo método con independencia de la etiqueta que elija el usuario.  El método del controlador de eventos necesita saber qué etiqueta se ha elegido, de forma que usa el nombre **sender** para identificar el control de la etiqueta.  La primera línea del método indica al programa que no es solo un objeto genérico, sino que es, en concreto, un control Label y que, a través del nombre **clickedLabel**, tiene acceso a las propiedades y métodos de la etiqueta.  
  
     Este método comprueba primero si **clickedLabel** se convirtió \(mediante conversión de tipos\) correctamente de un objeto en un control Label.  Si no, tiene un valor `null` \(C\#\) o `Nothing` \(Visual Basic\) y no es preciso ejecutar el resto del código del método.  Luego, el método comprueba el color del texto de la etiqueta elegida mediante la propiedad **ForeColor** de la etiqueta.  Si el color del texto de la etiqueta es negro, significa que el icono ya se ha elegido y el método ha terminado. \(Esto es lo que hace la instrucción `return`: indicar al programa que deje de ejecutar el método\). Si no, el icono no se ha elegido, por lo que el programa cambia el color del texto de la etiqueta a negro.  
  
6.  En la barra de menús, elija **Archivo**, **Guardar todo** para guardar el progreso y, a continuación, en la barra de menús, elija **Depurar**, **Iniciar depuración** para ejecutar el programa.  Debería ver un formulario vacío con un fondo azul.  Al elegir cualquiera de las celdas del formulario, uno de los iconos debería hacerse visible.  Siga eligiendo distintas partes del formulario.  A medida que elija los iconos, estos deberían mostrarse.  
  
### Para continuar o revisar  
  
-   Para ir al siguiente paso del tutorial, vea [Paso 5: Agregar referencias a etiquetas](../ide/step-5-add-label-references.md).  
  
-   Para volver al paso anterior del tutorial, vea [Paso 3: Asignar un icono aleatorio a cada etiqueta](../ide/step-3-assign-a-random-icon-to-each-label.md).