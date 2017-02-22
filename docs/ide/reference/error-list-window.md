---
title: "Lista de errores (Ventana) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ErrorList"
helpviewer_keywords: 
  - "Lista de tareas"
  - "errores de compilación"
  - "Lista de errores (ventana)"
  - "errores [Visual Studio], ventana Lista de errores"
ms.assetid: b7f6d45a-733b-4ad8-bc2f-737a37509e56
caps.latest.revision: 32
caps.handback.revision: 32
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Lista de errores (Ventana)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!NOTE]
>  La Lista de errores muestra información sobre un mensaje de error específico.  Puede copiar el número de error o el texto de la cadena de error de la ventana de salida.  Para mostrar la ventana de salida, presione Ctrl\+Alt\+O.  Consulte [Resultados \(Ventana\)](../../ide/reference/output-window.md).  
  
 La ventana **Lista de errores** permite desarrollar aplicaciones de forma más rápida.  Por ejemplo, puede realizar las tareas siguientes:  
  
-   Mostrar los errores, las advertencias y los mensajes que se generan mientras escribe el código.  
  
-   Buscar errores de sintaxis detectados por IntelliSense.  
  
-   Buscar errores de implementación, ciertos errores de análisis estático y errores detectados mientras se aplican directivas de Enterprise Templates.  
  
-   Hacer doble clic en la entrada de cualquier mensaje de error para abrir el archivo donde se produce el problema y desplazarse a la ubicación del error.  
  
-   Filtrar las entradas que se muestran y las columnas de información que aparecen para cada entrada.  
  
-   Buscar términos específicos y delimitar la búsqueda solo al proyecto o documento actual.  
  
 Para mostrar la **Lista de errores**, haga clic en **Ver\/Lista de errores** o **CTRL\+\\\+E**.  
  
 Puede elegir las pestañas **Errores**, **Advertencias** y **Mensajes** para ver diferentes niveles de información.  
  
 Para ordenar la lista, haga clic en cualquier encabezado de columna.  Para ordenar de nuevo por otra columna, mantenga presionada la tecla MAYÚS y haga clic en otro encabezado de columna.  Para seleccionar las columnas que se muestran y las que están ocultas, elija **Mostrar columnas** en el menú contextual.  Si desea cambiar el orden en el que se muestran las columnas, arrastre cualquier encabezado de columna hacia la izquierda o la derecha.  
  
> [!NOTE]
>  Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos aquí, en función de los valores de configuración o de edición activos.  Para cambiar su configuración, haga clic en **Herramientas\/Importar y exportar configuraciones**.  Para obtener más información, consulte [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/es-es/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Filtros de la lista de errores  
 Hay dos tipos de filtro en dos listas desplegables, una en el lado derecho de la barra de herramientas y otra a la izquierda de la barra de herramientas.  La lista desplegable del lado izquierdo de la barra de herramientas especifica el conjunto de archivos de código que se va a utilizar \(**Toda la solución**, **Documentos abiertos**, **Proyecto actual** o **Documento actual**\).  
  
 Puede limitar el ámbito de búsqueda para analizar y actuar en grupos de errores.  Por ejemplo, puede que desee centrarse en los errores más importantes que están impidiendo que un proyecto se compile.  Entre las opciones para delimitar el ámbito se incluyen las siguientes:  
  
1.  **Documentos abiertos**: muestra los errores, las advertencias y los mensajes de los documentos abiertos.  
  
2.  **Proyecto actual**: muestra los errores, las advertencias y los mensajes del proyecto del documento seleccionado actualmente en el **Editor** o del proyecto seleccionado en el **Explorador de soluciones**.  
  
    > [!NOTE]
    >  La lista filtrada de errores, advertencias y mensajes cambia si el proyecto del documento seleccionado actualmente es diferente al proyecto seleccionado en el **Explorador de soluciones**.  
  
3.  **Documento actual**: muestra los errores, las advertencias y los mensajes del documento seleccionado actualmente en el **Editor** o en el **Explorador de soluciones**.  
  
 Si se aplica un filtro actualmente al resultado de la búsqueda, el nombre del filtro aparece en la barra de título de **Lista de errores**.  A continuación, los botones **Errores**, **Advertencias** y **Mensajes** muestran el número de elementos filtrados junto con el número total de elementos, por ejemplo, los botones muestran x de y errores.  Si no se aplica ningún filtro, en la barra de título solo aparece "Lista de errores”.  
  
 La lista que se muestra en el lado derecho de la barra de herramientas especifica si se muestran los errores desde la compilación \(los errores resultantes de una operación de compilación\), desde IntelliSense \(los errores detectados antes de ejecutar una compilación\) o desde ambos.  
  
## Buscar  
 Utilice el cuadro de texto **Lista de errores de búsqueda** en el lado derecho de la barra de herramientas **Lista de errores** para buscar errores específicos en la lista de errores.  Puede buscar en cualquier columna visible de la lista de errores. Los resultados de la búsqueda siempre se ordenan en función de la columna que tenga prioridad de ordenación en lugar de la consulta o el filtro aplicado.  Si presiona la tecla **Esc** mientras el foco está en la **Lista de errores**, se borra el término de búsqueda y los resultados filtrados de la búsqueda.  También puede hacer clic en la **X** que se muestra en el lado derecho del cuadro de texto para borrarlos.  
  
## Guardar  
 Puede copiar la lista de errores y guardarla en un archivo.  Seleccione los errores que desea copiar, haga clic con el botón secundario en la selección y, a continuación, seleccione **Copiar** en el menú contextual.  Después puede pegar los errores en un archivo.  Si pega los errores en una hoja de cálculo de Excel, los campos aparecen como columnas diferentes.  
  
## Lista de elementos de la interfaz de usuario  
 Gravedad  
 Muestra los diferentes tipos de entrada de la **Lista de errores** \(**Error**, **Mensaje**, **Advertencia**, **Advertencia \(activa\)** y **Advertencia \(inactiva\)**.  
  
 Código  
 Muestra el código del error.  
  
 Descripción  
 Muestra el texto de la entrada.  
  
 Project  
 Muestra el nombre del proyecto actual.  
  
 Archivo  
 Muestra el nombre del archivo.  
  
 Línea  
 Muestra la línea en la que se produce el problema.