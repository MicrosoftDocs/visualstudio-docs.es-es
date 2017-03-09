---
title: "Ver valores de datos en sugerencias de datos en el editor de c&#243;digo | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
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
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Información sobre datos (herramienta)"
  - "depurar [Visual Studio], información sobre datos"
ms.assetid: ffa7bd18-439b-4685-a9b3-c7884b5de41f
caps.latest.revision: 38
caps.handback.revision: 38
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Ver valores de datos en sugerencias de datos en el editor de c&#243;digo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La Información sobre datos es una manera útil de ver información sobre las variables del programa durante la depuración.  La Información sobre datos funciona únicamente en modo de interrupción y únicamente con las variables que están dentro del actual ámbito de ejecución.  
  
 En [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)], la Información sobre datos se puede anclar en una ubicación concreta de un archivo de origen de datos o puede flotar encima de las ventanas de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
### Para mostrar la Información sobre datos solo en modo de interrupción  
  
1.  En una ventana de código fuente, coloque el puntero del mouse sobre cualquier variable en el ámbito actual.  
  
     Aparece la Información sobre datos.  
  
    > [!NOTE]
    >  Las informaciones sobre datos siempre se evalúan en el contexto en el que se suspende la ejecución, y no en el que el cursor se mantiene sobre un elemento.  Si mantiene el cursor sobre una variable en otra función con el mismo nombre que una variable que está en el contexto actual, el valor de la variable de la otra función se mostrará como el valor de la variable del contexto actual.  
  
2.  La Información sobre datos desaparece al quitar el puntero del mouse.  Para anclar la Información sobre datos para que permanezca abierta, haga clic en el icono **Anclar a origen**, o bien  
  
    -   Haga clic con el botón secundario en una variable y, a continuación, haga clic en **Anclar a origen**.  
  
     La Información sobre datos se cierra cuando la sesión de depuración finaliza.  
  
### Desanclar la Información sobre datos y dejar que flote  
  
-   En una Información sobre datos anclada, haga clic en el icono **Desanclar del origen**.  
  
     El icono pasa a la posición desanclada.  La Información sobre datos flota ahora sobre las ventanas abiertas.  La Información sobre datos que flota se cierra cuando la sesión de depuración finaliza.  
  
### Para volver a anclar una Información sobre datos flotante  
  
-   En una Información sobre datos, haga clic en el icono de anclaje.  
  
     El icono pasa a la posición anclada.  Si la Información sobre datos está fuera de una ventana de código fuente, el icono está deshabilitado y no se puede anclar.  
  
### Para cerrar una Información sobre datos  
  
-   Coloque el puntero del mouse sobre una Información sobre datos y, a continuación, haga clic en el icono **Cerrar**.  
  
### Para cerrar toda la Información sobre datos  
  
-   En el menú **Depurar**, haga clic en **Borrar toda la información sobre datos**.  
  
### Para cerrar toda la información sobre datos de un archivo concreto  
  
-   En el menú **Depurar**, haga clic en **Borrar toda la información sobre datos anclada a** *File*.  
  
## Expandir y editar información  
 Con la Información sobre datos, se puede expandir una matriz, una estructura o un objeto para ver sus miembros.  También se puede editar el valor de una variable de una Información sobre datos.  
  
#### Para expandir una variable y ver sus elementos  
  
-   En una información sobre datos, sitúe el puntero del mouse sobre el signo **\+** que precede al nombre de variable.  
  
     La variable se expande y se muestran sus elementos en forma de árbol.  
  
     Cuando la variable está expandida, puede utilizar las teclas de dirección en el teclado para desplazarse de arriba abajo.  También puede utilizar el mouse.  
  
#### Para modificar el valor de una variable mediante la Información sobre datos  
  
1.  En una Información sobre datos, haga clic en el valor.  En los valores de solo lectura, no está habilitado.  
  
2.  Escriba el nuevo valor y presione ENTRAR.  
  
## Configurar una Información sobre datos como transparente  
 Si desea ver el código que está detrás de una Información sobre datos, puede configurar temporalmente dicha información como transparente.  Esto no se aplica a la información sobre datos cuando está anclada o flota.  
  
#### Para configurar una Información sobre datos como transparente  
  
-   En una Información sobre datos, presione CTRL.  
  
     La Información sobre datos permanecerá transparente mientras mantenga presionada la tecla CTRL.  
  
## Visualizar tipos de datos complejos  
 Si aparece un icono de lupa junto a un nombre de variable en una Información sobre datos, hay uno o varios [Visualizadores](../debugger/create-custom-visualizers-of-data.md) disponibles para las variables de ese tipo de datos.  Los visualizadores se pueden utilizar para mostrar la información de manera más significativa, normalmente de forma gráfica.  
  
#### Para ver el contenido de una variable mediante un visualizador  
  
-   Haga clic en el icono de lupa para seleccionar el visualizador predeterminado del tipo de datos.  
  
     O bien  
  
     Haga clic en la flecha emergente junto al visualizador para seleccionar una lista emergente de visualizadores adecuados para el tipo de datos.  
  
     Un visualizador muestra la información.  
  
## Agregar información a una ventana Inspección  
 Si desea seguir examinando una variable, puede agregarla a la ventana **Inspección** desde la Información sobre datos.  
  
#### Para agregar una variable a la ventana Inspección  
  
-   Haga clic con el botón secundario en una Información sobre datos y, a continuación, haga clic en **Agregar inspección**.  
  
     La variable se agrega a la ventana **Inspección**.  Si utiliza una versión que admite varias ventanas **Inspección**, la variable se agrega a la ventana **Inspección 1**.  
  
## Importar y exportar Información sobre datos  
 Puede exportar Información sobre datos a un archivo XML, que puede compartir con un colega o modificar con un editor de texto.  
  
#### Para exportar información sobre datos  
  
1.  En el menú Depurar, haga clic en **Exportar información sobre datos**.  
  
     Aparece el cuadro de diálogo **Exportar información sobre datos**.  
  
2.  Utilice las técnicas del archivo estándar para navegar hasta la ubicación donde desea guardar el archivo XML, escriba un nombre para el archivo en el cuadro **Nombre de archivo** y, a continuación, haga clic en **Aceptar**.  
  
#### Para importar información sobre datos  
  
1.  En el menú Depurar, haga clic en **Importar información sobre datos**.  
  
     Aparece el cuadro de diálogo **Importar información sobre datos**.  
  
2.  Utilice el cuadro de diálogo para buscar el archivo XML que desea abrir y haga clic en **Aceptar**.  
  
## Vea también  
 [Ver datos en el depurador](../debugger/viewing-data-in-the-debugger.md)   
 [Cómo: Utilizar el cuadro de diálogo Inspección rápida](../Topic/How%20to:%20Use%20the%20QuickWatch%20Dialog%20Box.md)   
 [Visualizadores](../debugger/create-custom-visualizers-of-data.md)   
 [Cómo: Cambiar el formato numérico de las ventanas del depurador](../Topic/How%20to:%20Change%20the%20Numeric%20Format%20of%20Debugger%20Windows.md)