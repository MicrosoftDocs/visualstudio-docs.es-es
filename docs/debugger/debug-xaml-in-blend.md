---
title: "Depurar XAML en Blend | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 29a37182-2a2c-47e4-a4a9-2d5412738fed
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Depurar XAML en Blend
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede usar las herramientas de [!INCLUDE[blend_first](../debugger/includes/blend_first_md.md)] para depurar el código XAML de su aplicación.  Cuando compilas un proyecto, los errores se muestran en el panel **Resultados**.  Haz doble clic en un error para buscar el marcado relacionado con el error.  Si necesitas más espacio para trabajar, puedes ocultar el panel **Resultados** presionando F12.  
  
## Errores de sintaxis  
 Los errores de sintaxis se producen cuando el código XAML o los archivos de código subyacente no cumplen las reglas de formato del lenguaje.  La descripción del error puede ayudarte a solucionarlo.  La lista especifica también el nombre del archivo y el número de línea en que se produce el error.  Los errores de XAML se muestran en la pestaña **Marcado** en el panel **Resultados**.  
  
> [!TIP]
>  XAML es un lenguaje de marcado basado en XML y sigue las reglas sintácticas de XML.  
  
 Entre las causas comunes de errores de sintaxis de XAML, figuran las siguientes:  
  
-   Una palabra clave tiene errores ortográficos o el uso de las mayúsculas no es correcto.  
  
-   Faltan las comillas en atributos o cadenas de texto.  
  
-   A un elemento XAML le falta una etiqueta de cierre.  
  
-   Un elemento XAML está en una ubicación no permitida.  
  
 Para obtener más información sobre sintaxis XAML común, consulte [Guía de sintaxis XAML básica](http://go.microsoft.com/fwlink/?LinkId=329942).  
  
 También puedes identificar y resolver errores de sintaxis simples del código subyacente, errores de compilación y errores en tiempo de ejecución en [!INCLUDE[blend_subs](../debugger/includes/blend_subs_md.md)].  Pero puede que te resulte más fácil identificar y resolver los errores del código subyacente en Visual Studio.  
  
### Depurar código XAML de ejemplo  
 El ejemplo siguiente te guiará por una sesión de depuración de XAML sencilla en [!INCLUDE[blend_subs](../debugger/includes/blend_subs_md.md)].  
  
##### Para crear un proyecto  
  
1.  En [!INCLUDE[blend_subs](../debugger/includes/blend_subs_md.md)], abre el menú **Archivo** y haz clic en **Nuevo proyecto**.  
  
     En el cuadro de diálogo **Nuevo proyecto**, aparece a la izquierda una lista de tipos de proyecto.  Cuando hagas clic en un tipo de proyecto, las plantillas de proyecto asociadas a ese tipo aparecerán a la derecha.  
  
2.  En la lista de tipos de proyecto, haz clic en **XAML \(Tienda Windows\)**.  
  
3.  En la lista de plantillas de proyecto, haz clic en **Aplicación vacía**.  
  
4.  En el cuadro de texto **Nombre**, escribe `DebuggingSample`.  
  
5.  En el cuadro de texto **Ubicación**, comprueba la ubicación del proyecto.  
  
6.  En la lista **Lenguaje**, haz clic en **Visual C\#** y después en **Aceptar** para crear el proyecto.  
  
7.  Haz clic con el botón secundario en la superficie de diseño y haz clic en **Ver código fuente** para cambiar a la vista **Dos paneles**.  
  
8.  Copie el código siguiente al hacer clic en el vínculo **Copiar** de la esquina superior derecha del código.  
  
    ```  
    <Grid HorizontalAlignment="Left" Height="222" VerticalAlignment="Top>  
         <Button content="Button" x:Mame="Home" HorizontalAlignment="Left" VerticalAlignment="Top"/>  
         <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,38,0,0">  
         <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,75,0,0"/>  
         <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,112,0,0"/>  
         <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top Margin="0,149,0,0"/>  
    </Grid>  
  
    ```  
  
9. Busca la **cuadrícula** predeterminada y pega el código entre las etiquetas de apertura y cierre de la **cuadrícula**.  Cuando termines, el código debe tener un aspecto similar al siguiente:  
  
    ```  
    <Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">  
         <Grid HorizontalAlignment="Left" Height="222" VerticalAlignment="Top>  
              <Button content="Button" x:Mame="Home" HorizontalAlignment="Left" VerticalAlignment="Top"/>  
              <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,38,0,0">  
              <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,75,0,0"/>  
              <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,112,0,0"/>  
              <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top Margin="0,149,0,0"/>  
         </Grid>  
    </Grid>  
  
    ```  
  
10. Presiona Ctrl\+Mayús\+B para compilar el proyecto.  
  
 Aparece un mensaje de error para avisarle de que el proyecto no se puede compilar, y el panel **Resultados** con los errores aparece en la parte inferior de la aplicación.  
  
 ![Depurar XAML en Blend para Visual Studio](../debugger/media/blend_debugxaml_xaml.png "blend\_debugXAML\_XAML")  
  
### Resolver errores de XAML  
 Cuando se detectan errores de XAML, la superficie de diseño muestra una alerta de que el proyecto contiene marcado no válido.  La lista de errores del panel **Resultados** se actualiza conforme resuelves los errores.  Cuando haya resuelto todos los errores, se habilitará la superficie de diseño y su aplicación se mostrará en ella.  
  
##### Para resolver los errores de XAML  
  
1.  Haz doble clic en el primer error de la lista.  La descripción es "El valor '\<' no es válido en un atributo". Al hacer doble clic en el error, el puntero busca la ubicación correspondiente en el código.  El elemento `<` que aparece delante de `Button` es válido, y no es un atributo como se indica en el mensaje de error.  Si examinas la línea de código anterior, observarás que faltan las comillas de cierre del atributo `Top`.  Escribe las comillas de cierre.  Observa que la lista de errores del panel **Resultados** se actualiza para reflejar los cambios.  
  
2.  Haz doble clic en la descripción "'0' no es válido al principio de un nombre". `Margin="0,149,0,0"` parece que tiene el formato correcto.  De todos modos, observa que la codificación de color de `Margin` no coincide con las demás instancias de `Margin` en el código.  Como faltan las comillas de cierre del par de nombre\-valor anterior \(`VerticalAlignment="Top`\), `Margin="` se interpreta como parte del valor del atributo anterior y 0, como el principio de un par nombre\-valor.  Escribe las comillas de cierre de `Top`.  La lista de errores del panel **Resultados** se actualiza para reflejar los cambios.  
  
3.  Haz doble clic en el otro error: "La etiqueta XML de cierre 'Button' no tiene una etiqueta de apertura correspondiente". El puntero se coloca en la etiqueta **Grid** de cierre \(`</Grid>`\), lo que sugiere que el error está dentro del objeto `Grid`.  Observa que al segundo objeto `Button` le falta la etiqueta de cierre.  Cuando agregues la `/` de cierre, la lista del panel **Resultados** se actualizará.  Ahora que se han resuelto estos errores iniciales, se han identificado dos errores más.  
  
4.  Haz doble clic en "No se reconoce o no se puede tener acceso al miembro 'content'". La c `c` de `content` debería estar en mayúsculas.  Sustituye la "c" minúscula por una "c" mayúscula.  
  
5.  Haz doble clic en "La propiedad 'Mame' no existe en el espacio de nombres 'http:\/\/schemas.microsoft.com\/winfx\/2006\/xaml'". La "M" de "Mame" debería ser una "N". Sustituya la "M" por una "N". Ahora que el XAML se puede analizar, la aplicación aparece en la superficie de diseño.  
  
     ![Depuración de XAML en Blend para Visual Studio](../debugger/media/blend_debugartboard_xaml.png "blend\_debugArtboard\_XAML")  
  
     Presiona Ctrl\+Mayús\+B para compilar el proyecto y confirmar que no queda ningún error.  
  
## Depurar en Visual Studio  
 Puede abrir proyectos de [!INCLUDE[blend_subs](../debugger/includes/blend_subs_md.md)] en Visual Studio para depurar el código de su aplicación más fácilmente.  Para abrir un proyecto de [!INCLUDE[blend_subs](../debugger/includes/blend_subs_md.md)] en Visual Studio, haz clic con el botón secundario en el proyecto en el panel **Proyectos** y después haz clic en **Editar en Visual Studio**.  Cuando termine la sesión de depuración en Visual Studio, presione Ctrl\+Mayús\+S para guardar todos los cambios y después vuelva a [!INCLUDE[blend_subs](../debugger/includes/blend_subs_md.md)].  Se te preguntará si deseas recargar el proyecto.  Haz clic en **Sí a todo** para continuar trabajando en [!INCLUDE[blend_subs](../debugger/includes/blend_subs_md.md)].  
  
 Para obtener más información sobre la depuración de la aplicación, consulte [Depurar aplicaciones de la Tienda Windows en Visual Studio](http://go.microsoft.com/fwlink/?LinkId=329944).  
  
## Obtener ayuda  
 Si necesita más ayuda para depurar la aplicación de [!INCLUDE[blend_subs](../debugger/includes/blend_subs_md.md)], puede buscar entradas relacionadas con su problema o publicar una pregunta en los [foros de la comunidad de aplicaciones de la Tienda Windows](http://go.microsoft.com/fwlink/?LinkId=280308).