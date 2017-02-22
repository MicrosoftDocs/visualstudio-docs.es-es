---
title: "Buscar y reemplazar texto | Microsoft Docs"
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
  - "vs.find"
  - "vs.findreplacecontrol"
  - "vs.findreplace.findsymbol"
  - "vs.findreplace.symbol"
  - "findresultswindow"
  - "vs.findreplace.quickreplace"
  - "vs.findsymbol"
  - "vs.findinfiles"
  - "vs.findresults1"
  - "vs,findsymbolwindow"
  - "vs.findreplace.quickfind"
  - "vs.lookin"
  - "vs.replace"
helpviewer_keywords: 
  - "find"
  - "buscar y reemplazar"
  - "Buscar en archivos (cuadro de diálogo)"
  - "buscar texto"
  - "find, symbol"
  - "find, texto"
  - "replace"
  - "Reemplazar (cuadro de diálogo)"
  - "Reemplazar en archivos (cuadro de diálogo)"
  - "reemplazar texto"
  - "búsquedas de texto"
  - "búsquedas de texto, buscar y reemplazar texto"
  - "texto, buscar y reemplazar"
ms.assetid: a62545c3-1570-4d12-99fb-a82607eb35a1
caps.latest.revision: 31
caps.handback.revision: 31
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Buscar y reemplazar texto
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede buscar y reemplazar texto en el editor de código de Visual Studio, y determinadas ventanas de resultados basadas en texto como las ventanas **Resultados de la búsqueda**, utilizando el control **Buscar y reemplazar** o **Buscar\/reemplazar en archivos**.  También puede buscar y reemplazar en algunas ventanas del diseñador, como el diseñador XAML y el diseñador de Windows Forms, y ventanas de herramientas  
  
 Puede establecer el ámbito de las búsquedas al documento actual, la solución actual o a un conjunto personalizado de carpetas.  También puede especificar un conjunto de extensiones de nombre de archivo para las búsquedas de varios archivos.  Puede personalizar la sintaxis de búsqueda con expresiones regulares .NET.  
  
 Para buscar y reemplazar expresiones regulares, vea [Usar expresiones regulares en Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).  
  
> [!TIP]
>  La casilla **Buscar\/Comando** aún está disponible como control de barra de herramientas, pero ya no es visible de manera predeterminada.  Puede mostrar el cuadro **Buscar\/Comando** eligiendo **Agregar o quitar botones** en la barra de herramientas **Estándar** y eligiendo **Buscar**.  Para obtener más información, vea [Cuadro Buscar\/Comando](../ide/find-command-box.md).  
  
## Control Buscar y reemplazar  
 El control **Buscar y reemplazar** aparece en la esquina superior derecha de la ventana Editor de código.  El control **Buscar y reemplazar** resalta inmediatamente cada aparición de la cadena de búsqueda especificada en el documento actual.  Puede navegar de una aparición a otra eligiendo el botón **Buscar siguiente** o el botón **Buscar anterior** en el control de búsqueda.  
  
 Puede tener acceso a opciones de reemplazo eligiendo el botón situado junto al cuadro de texto **Buscar**.  Para realizar un reemplazo cada vez, elija el botón **Reemplazar siguiente** junto al cuadro de texto **Reemplazar**.  Para reemplazar todas las coincidencias, elija el botón **Reemplazar todo**.  
  
 Para cambiar el color de resaltado de las coincidencias, elija el menú **Herramientas**, seleccione **Opciones**, elija **Entorno** y seleccione **Fuentes y colores**.  En la lista **Mostrar valores para**, seleccione **Editor de texto** y, en la lista **Mostrar los elementos**, seleccione **Buscar elementos resaltados \(extensión\)**.  
  
### Buscar ventanas de herramientas  
 Puede utilizar el control **Buscar** en ventanas de código o texto, como las ventanas **Salida** y las ventanas **Resultados de la búsqueda**, eligiendo **Buscar y reemplazar** en el menú **Editar** o \(Ctrl\+F\).  
  
 También encontrará una versión del control Find en algunas ventanas de herramientas.  Por ejemplo, puede filtrar la lista de controles en la ventana **Cuadro de herramientas** especificando texto en el cuadro de búsqueda.  Otras ventanas de herramientas que ahora permiten buscar en su contenido incluyen **Explorador de soluciones**, la ventana **Propiedades** y **Team Explorer**, entre otras.  
  
## Buscar\/reemplazar en archivos  
 **Buscar y reemplazar en archivos** funciona como el control **Buscar y reemplazar**, salvo que puede definir un ámbito para la búsqueda.  No solo puede buscar en el archivo abierto en el editor, sino que también puede buscar en todos los documentos abiertos, en toda la solución, en el proyecto actual y en los conjuntos de carpeta seleccionados.  También puede buscar por la extensión de nombre de archivo.  Para tener acceso al cuadro de diálogo **Buscar y reemplazar en archivos**, elija **Buscar y reemplazar** en el menú **Editar** \(o CTRL\+MAYÚS\+F\).  
  
 Cuando elija **Buscar todos**, aparecerá una ventana **Resultados de la búsqueda** en la que se mostrarán las coincidencias de la búsqueda.  Seleccionar un resultado en la lista muestra el archivo asociado y resalta la coincidencia.  Si el archivo no está abierto para editarlo, este se abrirá en una pestaña de vista previa a la derecha del cuadro de la pestaña.  Puede utilizar el control **Buscar** para buscar a través de la lista **Resultados de la búsqueda**.  
  
### Creación de conjuntos de carpeta de búsqueda personalizados  
 Puede definir un ámbito de búsqueda eligiendo el botón **Elegir carpetas de búsqueda** \(parece **…**\) situado junto al cuadro **Buscar en**.  En el cuadro **Elegir carpetas de búsqueda**, puede especificar un conjunto de carpetas en las que buscar y puede guardar la especificación para poder reutilizarla posteriormente.  Puede especificar carpetas en un equipo remoto solo si ha asignado su unidad al equipo local.  
  
### Creación de conjuntos de componentes personalizados  
 Puede definir conjuntos de componentes como su ámbito de búsqueda eligiendo el botón **Editar conjunto de componentes personalizado** que se encuentra junto al cuadro **Buscar en**.  Puede especificar componentes de .NET o COM instalados, proyectos de Visual Studio incluidos en su solución o cualquier ensamblado o biblioteca de tipos \(.dll, .tlb, .olb, .exe u .ocx\).  Para buscar referencias, active la casilla **Buscar en referencias**.  
  
## Vea también  
 [Usar expresiones regulares en Visual Studio](../ide/using-regular-expressions-in-visual-studio.md)