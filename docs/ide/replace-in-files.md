---
title: "Reemplazar en archivos | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.findreplace.replaceinfiles"
  - "vs.replaceinfiles"
helpviewer_keywords: 
  - "búsquedas de texto, reemplazar texto"
  - "Ventana Buscar y reemplazar, pestaña Reemplazar en archivos"
  - "Pestaña Reemplazar en archivos, ventana Buscar y reemplazar"
ms.assetid: ca361466-53bd-44db-a28a-3a74bc03b028
caps.latest.revision: 29
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 29
---
# Reemplazar en archivos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

**Reemplazar en archivos** permite buscar una cadena o expresión en el código de un conjunto de archivos especificado, así como cambiar algunas o todas las coincidencias encontradas.  Estas coincidencias y las acciones emprendidas se muestran en la ventana **Resultados de la búsqueda** seleccionada en **Opciones de resultado**.  
  
> [!NOTE]
>  Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos.  Para cambiar su configuración, elija Importar y exportar configuraciones en el menú Herramientas.  Para obtener más información, vea [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/es-es/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Puede utilizar cualquiera de los métodos siguientes para que se muestre la opción **Reemplazar en archivos** de la ventana **Buscar y reemplazar**.  
  
### Para mostrar Reemplazar en archivos  
  
1.  En el menú **Editar**, expanda **Buscar y reemplazar**.  
  
2.  Elija **Reemplazar en archivos**  
  
     \-O bien\-  
  
     Si el  **Buscar y reemplazar** ventana ya está abierta, en la barra de herramientas, elija  **Reemplazar en archivos**.  
  
## Buscar  
 Para buscar una nueva cadena de texto o expresión, especifique en el cuadro.  Para buscar cualquiera de las cadenas de 20 que ha buscado más recientemente, abra la lista y seleccione la cadena para el que desea buscar.  Elija el adyacentes  **Generador de expresiones** botón si desea utilizar una o varias expresiones regulares en la cadena de búsqueda.  Para obtener más información, vea [Usar expresiones regulares en Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).  
  
## Reemplazar con  
 Para reemplazar las instancias de la cadena en el  **Buscar** con otra cadena, escriba la cadena de reemplazo en el  **Reemplazar por** cuadro.  Para eliminar las instancias de la cadena en el  **Buscar** cuadro de diálogo, deje este campo en blanco.  Abra la lista para mostrar las cadenas de 20 por el que busca más recientemente.  Elija el adyacentes  **Generador de expresiones** botón si desea utilizar una o varias expresiones regulares en la cadena de reemplazo.  Para obtener más información, vea [Usar expresiones regulares en Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).  
  
## Buscar en  
 La opción elegida en la lista desplegable **Buscar en** determina si **Reemplazar en archivos** busca sólo en los archivos activos actualmente o en todos los archivos almacenados en algunas carpetas.  Seleccione un ámbito de búsqueda en la lista, escriba una ruta de carpeta o haga clic en el  **Examinar \(...\)** botón para mostrar la  **Elegir las carpetas de búsqueda** diálogo cuadro y elija un conjunto de carpetas para buscar.  También se puede escribir una ruta de acceso directamente en el cuadro **Buscar en**.  
  
> [!NOTE]
>  Si la opción **Buscar en** seleccionada provoca una búsqueda en un archivo que ha desprotegido del control de código fuente, sólo se buscará en la versión de ese archivo que se haya descargado en su equipo local.  
  
## Opciones de búsqueda  
 Puede expandir o contraer la sección **Opciones de búsqueda**.  Las siguientes opciones pueden activarse o desactivarse:  
  
 Coincidir mayúsculas y minúsculas  
 Cuando está seleccionada, las ventanas **Resultados de la búsqueda** sólo muestran las repeticiones de la cadena **Buscar** que coincidan tanto en contenido como en uso de mayúsculas y minúsculas.  Por ejemplo, una búsqueda de "MiObjeto" con la opción **Coincidir mayúsculas y minúsculas** seleccionada devolverá "MiObjeto" pero no "miobjeto" ni "MIOBJETO".  
  
 Sólo palabras completas  
 Cuando está seleccionada, las ventanas **Resultados de la búsqueda** sólo muestran las repeticiones de la cadena **Buscar** que coincidan con palabras completas.  Por ejemplo, una búsqueda de "MiObjeto" devolverá "MiObjeto" pero no "CMiObjeto."  
  
 Utilizar expresiones regulares  
 Cuando esta casilla de verificación está activada, puede utilizar las notaciones especiales para definir los patrones de texto en el  **Buscar** o  **Reemplazar con** cuadros de texto.  Para obtener una lista de estas notaciones, consulte [Usar expresiones regulares en Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).  
  
 Buscar en estos tipos de archivo  
 Esta lista indica los tipos de archivo en los que buscar en los directorios de **Buscar en**.  Si este campo está en blanco, se buscará en todos los archivos existentes en los directorios de esta opción.  
  
 Seleccione cualquier elemento de la lista para escribir una cadena de búsqueda preconfigurada que buscará en los archivos de esos tipos determinados.  
  
## Opciones de resultados  
 Puede expandir o contraer la sección **Opciones de resultados**.  Las siguientes opciones pueden activarse o desactivarse:  
  
 Ventana Resultados de la búsqueda 1  
 Cuando se selecciona esta opción, los resultados de la búsqueda actual reemplazarán el contenido de la ventana **Resultados de la búsqueda 1**.  Esta ventana se abre de forma automática para mostrar los resultados.  Para abrir esta ventana manualmente, seleccione **Otras ventanas** en el menú **Ver** y elija **Resultados de la búsqueda 1**.  
  
 Ventana Resultados de la búsqueda 2  
 Cuando se selecciona esta opción, los resultados de la búsqueda actual reemplazarán el contenido de la ventana **Resultados de la búsqueda 2**.  Esta ventana se abre de forma automática para mostrar los resultados.  Para abrir esta ventana manualmente, seleccione **Otras ventanas** en el menú **Ver** y elija **Resultados de la búsqueda 2**.  
  
 Mostrar sólo nombres de archivo  
 Cuando esta casilla de verificación está activada, las ventanas de resultados de la búsqueda indican los nombres completos y rutas de acceso para todos los archivos que contienen la cadena de búsqueda.  No obstante, los resultados no incluyen la línea de código donde aparece la cadena.  Esta casilla de verificación sólo está disponible para buscar en archivos.  
  
 Mantener los archivos modificados abiertos después de reemplazar todo  
 Cuando se selecciona, deja abiertos todos los archivos en los que se realizaron reemplazos; por tanto, puede deshacer o guardar los cambios.  Es posible que las restricciones de memoria limiten el número de archivos que pueden permanecer abiertos tras una operación de reemplazo.  
  
> [!CAUTION]
>  Sólo puede utilizar **Deshacer** en archivos que permanecen abiertos para su edición.  Si esta opción no está seleccionada, los archivos que no estaban ya abiertos para su edición permanecerán cerrados y no habrá ninguna opción **Deshacer** disponible en esos archivos.  
  
## Vea también  
 [Buscar y reemplazar texto](../ide/finding-and-replacing-text.md)   
 [Buscar en archivos](../ide/find-in-files.md)   
 [Comandos de Visual Studio](../ide/reference/visual-studio-commands.md)