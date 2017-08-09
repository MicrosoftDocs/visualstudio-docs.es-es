---
title: Live Unit Testing en Visual Studio | Microsoft Docs
ms.date: 2017-03-07
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio ALM
- Live Unit Testing
ms.assetid: 5b51fb96-94f4-4926-92b9-262156c05b85
author: rpetrusha
ms.author: ronpet
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: c559290c8e88c8b4e37feabc7014188fad15434d
ms.openlocfilehash: 0a939044b9806236cf55333c30bce24ae0fdb28a
ms.contentlocale: es-es
ms.lasthandoff: 06/08/2017

---

# <a name="live-unit-testing-with-visual-studio-2017"></a>Live Unit Testing con Visual Studio 2017

Mientras desarrolla una aplicación, Live Unit Testing ejecuta automáticamente y en segundo plano cualquier prueba unitaria afectada y presenta los resultados y la cobertura de código en vivo en el IDE de Visual Studio en tiempo real. Cuando modifica el código, Live Unit Testing proporciona comentarios sobre cómo los cambios afectaron a las pruebas existentes y si el código nuevo que ha agregado está cubierto por una o varias pruebas existentes. Esto le recordará que debe escribir pruebas unitarias cuando realiza correcciones de errores o agrega nuevas características.

> [!NOTE]
> Live Unit Testing está disponible para proyectos de C# y Visual Basic que tienen como destino .NET Core o .NET Framework en la edición Enterprise de Visual Studio 2017.

## <a name="supported-test-frameworks"></a>Marcos de prueba admitidos
Live Unit Testing funciona con los tres marcos de pruebas unitarias conocidos enumerados en la tabla siguiente. La versión mínima admitida de sus adaptadores y marcos también aparece en la tabla. Los marcos de pruebas unitarias están disponibles en NuGet.org.
 
<table> 
<tr>
   <th>Marco de prueba</th>
   <th>Versión mínima del adaptador de Visual Studio</th>
   <th>Versión mínima del marco</th>
</tr>
<tr>
   <td>xUnit.net</td>
   <td> xunit.runner.visualstudio version 2.2.0-beta3-build1187</td>
   <td>xunit 2.0</td> 
</tr>
<tr>
   <td>NUnit</td>
   <td>NUnit3TestAdapter version 3.5.1</td>  
   <td>NUnit version 3.5.0</td>
</tr>
<tr>
   <td>MSTest</td>
   <td>MSTest.TestAdapter 1.1.11</td>
   <td>MSTest.TestFramework 1.1.11</td>
</tr>
</table>

Si tiene un adaptador y referencias de marco de prueba antiguos de los proyectos existentes, asegúrese de quitarlos. (Si usa MSTest, asegúrese de quitar la referencia a `Microsoft.VisualStudio.QualityTools.UnitTestFramework`). Agregue los nuevos si Live Unit Testing no funciona para usted. 

En algunos casos, es posible que tenga que restaurar explícitamente los paquetes NuGet a los que los proyectos de la solución hacen referencia para que Live Unit Testing funcione. Puede hacerlo compilando explícitamente la solución (seleccione **Compilar**, **Recompilar solución** en el menú de Visual Studio de nivel superior) o restaurando los paquetes en la solución (haga doble clic en la solución y seleccione **Restaurar paquetes de NuGet**) antes de habilitar Live Unit Testing. 

#   <a name="configuring-live-unit-testing"></a>Configuración de Live Unit Testing

Puede configurar Live Unit Testing seleccionando **Herramientas**, **Opciones** en el menú de Visual Studio de nivel superior y luego seleccionando **Live Unit Testing** en el panel izquierdo del cuadro de diálogo **Opciones**. La figura siguiente muestra las opciones de configuración Live Unit Testing disponibles en el cuadro de diálogo.

  ![Imagen](./media/lut-options.png)

A continuación se indican las opciones que se pueden configurar:

- Si Live Unit Testing se ejecuta automáticamente cuando se abre una solución.
- Si Live Unit Testing se pausa cuando se compila y depura una solución, o cuando la energía de la batería del sistema cae por debajo de un umbral especificado.
- El intervalo después del cual un caso de prueba expira; el valor predeterminado es 30 segundos. 
- El número de procesos de prueba que Live Unit Testing crea. 
- El nivel de la información que se escribe en la ventana **Salida** de Live Unit Testing. Las opciones incluyen no registrar nada (Ninguno), solo los mensajes de error (Error), mensajes de error e informativos (Información, el valor predeterminado) o todos los detalles (Detallado).

También puede mostrar la salida detallada en la ventana **Salida** de Live Unit Testing asignando un valor de "1" a una variable de entorno de usuario denominada `VS_UTE_DIAGNOSTICS` y reiniciando Visual Studio. 

Para capturar mensajes de registro de MSBuild detallados desde Live Unit Testing en un archivo, establezca la variable de entorno de usuario `LiveUnitTesting_BuildLog` en el nombre del archivo que va a contener el registro.

## <a name="starting-pausing-and-stopping-live-unit-testing"></a>Inicio, pausa y detención de Live Unit Testing

Puede habilitar Live Unit Testing seleccionando **Prueba**, **Live Unit Testing**, **Iniciar** en el menú de Visual Studio de nivel superior. Cuando Live Unit Testing se habilita, las opciones disponibles en el menú **Live Unit Testing** pasan de un elemento único (**Iniciar**) a tres: **Pausar**, **Detener** y **Reiniciar**.

Live Unit Testing puede pausarse temporalmente o detenerse por completo en cualquier momento. Puede hacerlo, por ejemplo, si está en curso una refactorización y sabe que las pruebas se interrumpirán durante un tiempo. Las tres opciones de menú son:

- **Pausar**, que suspende temporalmente Live Unit Testing. 
    Cuando Live Unit Testing se pausa, la visualización de la cobertura no aparece en el editor, pero se conservan todos los datos recopilados. Para reanudar Live Unit Testing, seleccione "Continuar" en el menú Live Unit Testing. Live Unit Testing realizará el trabajo necesario para ponerse al día con todas las ediciones realizadas mientras estaba en pausa y actualizará los glifos apropiadamente. 
- **Detener**, para parar completamente Live Unit Testing. Live Unit Testing descarta todos los datos que ha recopilado.
- **Reiniciar**, que equivale a seleccionar **Detener** y después **Iniciar** en el menú **Live Unit Testing**.

##  <a name="viewing-coverage-visualization-in-the-editor-as-you-type"></a>Presentación de la visualización de la cobertura en el editor a medida que escribe

Cuando ya se ha habilitado, Live Unit Testing actualiza cada línea de código en el editor de Visual Studio para mostrar si el código que está escribiendo está cubierto por las pruebas unitarias y si las pruebas que cubre se superan.  La siguiente figura muestra líneas de código tanto con pruebas que se superan como con pruebas con error, así como líneas de código que no están cubiertas por las pruebas. Las líneas representadas con un símbolo "✓" de color verde solo están cubiertas por pruebas superadas, las líneas representadas con un símbolo "🞩" de color rojo están cubiertas por una o varias pruebas con error y las líneas representadas con un símbolo "" azul no están cubiertas por ninguna prueba.

  ![Imagen](./media/lut-codewindow.png)

La visualización de cobertura de Live Unit Testing se actualiza inmediatamente a medida que modifica el editor de código. Al procesar las ediciones, la visualización cambia para indicar que los datos no están actualizados agregando una imagen de cronómetro redondo debajo de los símbolos de superación, error y sin cubrir, como se muestra en la figura siguiente.

  ![Imagen](./media/lut-codeupdating.png)
 
## <a name="getting-information-on-successful-or-failed-tests"></a>Obtención de información sobre las pruebas superadas o con error

Al mantener el puntero sobre el símbolo de operación correcta o con error en la ventana de código, puede ver cuántas pruebas alcanzan esa línea. Si hace clic en el símbolo, puede ver el estado de las pruebas individuales, como se muestra en la figura siguiente.
 
  ![Imagen](./media/lut-failedinfo.png) 

Cuando mantiene el puntero sobre la prueba con error en la información sobre herramientas, se expande para proporcionar información adicional sobre el error, como se muestra en la imagen siguiente. Si hace clic en la prueba con error en la información sobre herramientas, puede navegar directamente a ella.

  ![Imagen](./media/lut-failedmsg.png) 

## <a name="diagnosing-and-correcting-test-failures"></a>Diagnóstico y corrección de pruebas con error

A partir de la prueba con error, puede depurar fácilmente el código del producto, realizar ediciones y continuar desarrollando la aplicación. Dado que Live Unit Testing se ejecuta en segundo plano, no es necesario detener y reiniciar Live Unit Testing durante el ciclo de depuración, edición y continuación.

Por ejemplo, el error de la prueba que se muestra en la figura anterior fue causado por una asunción incorrecta en el método de prueba de que caracteres no alfabéticos devolverían `true` cuando se pasaran al método [Char.IsLower](xref:System.Char.IsLower(System.Char)). Una vez corregido el método de prueba, todas las pruebas se superan. Mientras estamos haciendo esto, no tenemos que pausar o detener Live Unit Testing.

## <a name="live-unit-testing-and-test-explorer"></a>Live Unit Testing y el Explorador de pruebas

Normalmente, el **Explorador de pruebas** proporciona la interfaz que permite ejecutar, depurar y analizar los resultados de las pruebas. Live Unit Testing se integra con el **Explorador de pruebas**. Cuando la característica Live Unit Testing no está habilitada o está detenida, el **Explorador de pruebas** muestra el estado de las pruebas unitarias la última vez que se ejecutó una prueba. Los cambios de código fuente requieren que se vuelvan a ejecutar las pruebas. En cambio, cuando Live Unit Testing se ha habilitado, el estado de las pruebas unitarias en el **Explorador de pruebas** se actualiza inmediatamente. Ya no necesitará ejecutar las pruebas unitarias de forma explícita. 

Sin embargo, hay algunas diferencias entre la ejecución y actualización automáticas de resultados de pruebas en Live Unit Testing y la ejecución explícita de pruebas desde el **Explorador de pruebas**. Se incluyen los siguientes:

- La ejecución o depuración de pruebas desde la ventana Explorador de pruebas ejecuta binarios normales, mientras que Live Unit Testing ejecuta binarios instrumentados. 
- Live Unit Testing no crea un nuevo dominio de aplicación para ejecutar las pruebas, sino que ejecuta pruebas del dominio predeterminado. Las pruebas que se ejecutan desde la ventana **Explorador de pruebas** crean un nuevo dominio de aplicación.
- Live Unit Testing ejecuta pruebas secuencialmente en cada ensamblado de prueba. Si ejecuta varias pruebas desde la ventana **Explorador de pruebas** y selecciona el botón **Ejecutar pruebas en paralelo**, las pruebas se ejecutarán en paralelo.

## <a name="including-and-excluding-test-projects-and-test-methods"></a>Inclusión y exclusión de proyectos de prueba y métodos de prueba

Para soluciones con muchos proyectos de prueba, puede controlar qué proyectos y qué métodos individuales de un proyecto participan en Live Unit Testing. 

Por ejemplo, si tiene una solución con cientos de proyectos de prueba y puede seleccionar un conjunto de proyectos de prueba de destino para participar en Live Unit Testing. Para seleccionar proyectos individuales en pruebas unitarias, haga lo siguiente después de iniciar Live Unit Testing:

1.  Haga clic con el botón derecho en la solución en el Explorador de soluciones y elija **Live Tests** (Pruebas en vivo), **Excluir** para excluir toda la solución.
2.  Haga clic con el botón derecho en cada proyecto de prueba que desearía incluir en las pruebas y elija **Live Tests** (Pruebas en vivo), **Incluir**.
 
Utilice la ventana del editor de código para incluir o excluir métodos de prueba individuales. Haga clic con el botón derecho en la firma del método de prueba en la ventana del editor de código y seleccione **Live Tests** (Pruebas en vivo), **Incluir** o **Live Tests** (Pruebas en vivo), **Excluir**. 

Como alternativa, también puede aplicar el atributo [<ExcludeFromCodeCoverage>](https://msdn.microsoft.com/library/system.diagnostics.codeanalysis.excludefromcodecoverageattribute.aspx) para, mediante programación, excluir los métodos, las clases o las estructuras y evitar que informen de su cobertura en Live Unit Testing.

Live Unit Testing guarda el estado de inclusión o exclusión como una configuración de usuario y lo recuerda cuando una solución se cierra y se vuelve a abrir. 

## <a name="see-also"></a>Vea también

[Blog de Live Unit Testing](https://go.microsoft.com/fwlink/?linkid=842514)   
[Preguntas más frecuentes de Live Unit Testing](live-unit-testing-faq.md)    
[Vídeo de Channel 9: Live Unit Testing in Visual Studio 2017 (Live Unit Testing en Visual Studio 2017)](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T105)


