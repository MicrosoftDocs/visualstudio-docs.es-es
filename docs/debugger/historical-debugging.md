---
title: "Depuraci&#243;n hist&#243;rica | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7cc5ddf2-2f7c-4f83-b7ca-58e92e9bfdd2
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Depuraci&#243;n hist&#243;rica
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Depuración histórica es un modo de depuración que depende de la información recopilada por IntelliTrace.  Le permite desplazarse hacia atrás y hacia delante por la ejecución de la aplicación y comprobar su estado.  
  
 Puede usar IntelliTrace en Visual Studio Enterprise \(pero no en las ediciones Professional o Community\).  
  
## ¿Por qué usar Depuración histórica?  
 Establecer puntos de interrupción para encontrar errores puede ser cuestión de suerte.  Establezca un punto de interrupción cerca del lugar en el código donde sospecha que está el error y luego ejecute la aplicación en el depurador. Con suerte, se alcanzará el punto de interrupción en un lugar que revele el origen del error.  De lo contrario, tendrá que establecer un punto de interrupción en otro lugar del código y volver a ejecutar el depurador, y así una y otra vez hasta que encuentre el problema.  
  
 ![establecer un punto de interrupción](~/docs/debugger/media/breakpointprocesa.png "BreakpointProcesa")  
  
 Puede usar IntelliTrace y Depuración histórica para recorrer la aplicación e inspeccionar su estado \(pila de llamadas y variables locales\) sin tener que establecer puntos de interrupción, reiniciar la depuración y repetir los pasos de prueba.  Esto puede ahorrarle mucho tiempo, especialmente cuando el error se encuentra escondido en un escenario de prueba que se tarda en ejecutar.  
  
## ¿Cómo empiezo a usar Depuración histórica?  
 De forma predeterminada, IntelliTrace está habilitado.  Solo tiene que decidir qué eventos y llamadas de función le interesan.  Para obtener más información sobre cómo definir lo que quiere buscar, consulte [Características de IntelliTrace](../debugger/intellitrace-features.md).  Para ver una depuración paso a paso con IntelliTrace, consulte [Tutorial: Uso de IntelliTrace](../debugger/walkthrough-using-intellitrace.md).  
  
## Desplazarse por el código con Depuración histórica  
 Comencemos con un sencillo programa que tiene un error.  En una aplicación de consola C\#, agregue el código siguiente:  
  
```c#  
static void Main(string[] args)  
{  
    int testInt = 0;  
    int resultInt = AddAll(testInt);  
    Console.WriteLine(resultInt);  
}  
private static int AddAll(int j)  
{  
    for (int i = 0; i < 20; i++)  
    {  
        j = AddInt(j);  
    }  
    return j;  
}  
  
private static int AddInt(int add)  
{  
    if (add == 10)  
    {  
        return add += 25;  
    }  
    return ++add;  
}  
```  
  
 Supondremos que el valor esperado de `resultInt` después de llamar a `AddAll()` es 20 \(el resultado de incrementar `testInt` 20 veces\).  \(También supondremos que no puede ver el error en `AddInt()`\). Pero el resultado es 44.  ¿Cómo podemos encontrar el error sin pasar por `AddAll()` 10 veces?  Podemos usar Depuración histórica para encontrar el error de forma más rápida y sencilla.  Esta es la manera de hacerlo:  
  
1.  En Herramientas \/ Opciones \/ IntelliTrace \/ General, asegúrese de que IntelliTrace está habilitado y seleccione la opción de eventos de IntelliTrace e información de llamadas.  Si no selecciona esta opción, no podrá ver el medianil de navegación \(tal y como se explica más adelante\).  
  
2.  Establezca un punto de interrupción en la línea `Console.WriteLine(resultInt);`.  
  
3.  Inicie la depuración.  El código se ejecuta hasta el punto de interrupción.  En la ventana **Locales** puede ver que el valor de `resultInt` es 44.  
  
4.  Abra la ventana **Herramientas de diagnóstico** \(**Depurar \/ Mostrar herramientas de diagnóstico**\).  La ventana de código debe ser similar a la que se muestra a continuación:  
  
     ![Ventana de código en el punto de interrupción](~/docs/debugger/media/historicaldebuggingbreakpoint.png "HistoricalDebuggingBreakpoint")  
  
5.  Debería ver una flecha doble junto al margen izquierdo, justo encima del punto de interrupción.  Esta área se denomina medianil de navegación y se utiliza para Depuración histórica.  Haga clic en la flecha.  
  
     En la ventana de código, debería ver que la línea de código anterior \(`int resultInt = AddIterative(testInt);`\) es de color rosa.  Encima de la ventana verá un mensaje que indica que ya está en Depuración histórica.  
  
     La ventana de código ahora tiene el siguiente aspecto:  
  
     ![ventana de código en modo de depuración histórico](~/docs/debugger/media/historicaldebuggingback.png "HistoricalDebuggingBack")  
  
6.  Ahora puede depurar paso a paso por instrucciones el método `AddAll()` \(**F11**, o el botón **Paso a paso por instrucciones** en el medianil de navegación.  Avanzar paso a paso \(**F10**, o **Ir a llamada siguiente** en el medianil de navegación.  La línea rosa se encuentra ahora en la línea `j = AddInt(j);`.  En este caso, **F10** no avanza a la siguiente línea de código.  sino a la siguiente llamada de función.  Depuración histórica va de una llamada a otra y omite las líneas de código que no incluyen una llamada de función.  
  
7.  Ahora, depure paso a paso por instrucciones el método `AddInt()`.  Debería ver el error en este código inmediatamente.  
  
 Este procedimiento no ha hecho sino arañar la superficie de lo que se puede hacer con Depuración histórica.  Para obtener más información sobre las distintas configuraciones y los efectos de los botones diferentes en el medianil de navegación, consulte [Características de IntelliTrace](../debugger/intellitrace-features.md).