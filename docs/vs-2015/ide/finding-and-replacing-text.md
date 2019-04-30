---
title: Buscar y reemplazar texto | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.find
- vs.findreplacecontrol
- vs.findreplace.findsymbol
- vs.findreplace.symbol
- findresultswindow
- vs.findreplace.quickreplace
- vs.findsymbol
- vs.findinfiles
- vs.findresults1
- vs,findsymbolwindow
- vs.findreplace.quickfind
- vs.lookin
- vs.replace
helpviewer_keywords:
- text searches
- Replace in Files dialog box
- find, text
- Find in Files dialog box
- find
- text searches, finding and replacing text
- Replace dialog box
- text, finding and replacing
- find, symbol
- find and replace
- replace
- find text
- replacing text
ms.assetid: a62545c3-1570-4d12-99fb-a82607eb35a1
caps.latest.revision: 35
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 51d361bf74fb1181c64e5299b0925c262f185e9b
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63426333"
---
# <a name="finding-and-replacing-text"></a>Finding and Replacing Text
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede buscar y reemplazar texto en el editor de código de Visual Studio y en determinadas ventanas de salida basadas en texto como las ventanas **Resultados de la búsqueda**, con el control **Buscar y reemplazar** o **Buscar y reemplazar en archivos**. También puede buscar y reemplazar en algunas ventanas del diseñador, como el diseñador XAML y el diseñador de Windows Forms, y las ventanas de herramientas.  
  
 Puede definir el ámbito de las búsquedas en el documento actual, en la solución actual o en un conjunto personalizado de carpetas. También puede especificar un conjunto de extensiones de nombre de archivo para búsquedas de varios archivos. Puede personalizar la sintaxis de búsqueda mediante expresiones regulares .NET.  
  
 Para buscar y reemplazar expresiones regulares, vea [Usar expresiones regulares en Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).  
  
> [!TIP]
> El cuadro **Comando/Buscar** todavía está disponible como un control de la barra de herramientas, pero ya está visible de manera predeterminada. Puede mostrar el cuadro **Comando/Buscar** pulsando **Agregar o quitar botones** en la barra de herramientas **Estándar** y, después, pulsar **Buscar**. Para obtener más información, vea [Cuadro Comando/Buscar](../ide/find-command-box.md).  
  
## <a name="find-and-replace-control"></a>Control Buscar y reemplazar  
 El control **Buscar y reemplazar** aparece en la esquina superior derecha de la ventana del editor de código. El control **Buscar y reemplazar** resalta inmediatamente cada aparición de la cadena de búsqueda determinada en el documento actual. Puede ir de una aparición a otra pulsando el botón **Buscar siguiente** o en el botón **Buscar anterior** en el control de búsqueda.  
  
 Puede tener acceso a las opciones de reemplazo pulsando el botón siguiente al cuadro de texto **Buscar**. Para realizar un reemplazo puntual, pulse el botón **Reemplazar siguiente** junto al cuadro de texto **Reemplazar**. Para reemplazar todas las coincidencias, pulse el botón **Reemplazar todo**.  
  
 Para cambiar el color de resaltado de las coincidencias, pulse el menú **Herramientas**, seleccione **Opciones** y, después, pulse **Entorno** y **Fuentes y colores**. En la lista **Mostrar configuración para**, seleccione **Editor de texto** y, después, en la lista **Mostrar elementos**, seleccione **Buscar resaltado (Extensión)**.  
  
### <a name="searching-tool-windows"></a>Buscar ventanas de herramientas  
 Puede usar el control **Buscar** en ventanas de texto o código, como ventanas de **salida** y ventanas **Resultados de la búsqueda**, al pulsar **Buscar y reemplazar** en el menú **Edición** o (CTRL+F).  
  
 También está disponible una versión del control Buscar en algunas ventanas de herramientas. Por ejemplo, ahora puede filtrar la lista de controles en la ventana **Cuadro de herramientas** escribiendo texto en el cuadro de búsqueda. Otras ventanas de herramientas que ahora le permiten buscar su contenido incluyen **Explorador de soluciones**, la ventana **Propiedades** y **Team Explorer**, entre otras.  
  
## <a name="findreplace-in-files"></a>Buscar y reemplazar en archivos  
 **Buscar y reemplazar en archivos** funciona como el control **Buscar y reemplazar**, excepto que puede definir un ámbito para la búsqueda. No solo puede buscar el archivo abierto actual en el editor, sino que también puede buscar todos los documentos abiertos, la solución completa, el proyecto actual y los conjuntos de carpetas seleccionados. También puede buscar mediante la extensión del nombre de archivo. Para tener acceso al cuadro de diálogo **Buscar y reemplazar en archivos**, pulse **Buscar y reemplazar** en el menú **Edición** (o CTRL+SHIFT+F).  
  
 Cuando pulse **Buscar todo**, se abre una ventana **Buscar resultados** y se muestran las coincidencias de la búsqueda. Al seleccionar un resultado en la lista se muestra el archivo asociado y se resalta la coincidencia. Si el archivo todavía no está abierto para su edición, se abre en una pestaña de vista previa en el lateral derecho de la pestaña también. Puede usar el control **Buscar** para buscar en la lista **Resultados de la búsqueda**.  
  
### <a name="creating-custom-search-folder-sets"></a>Creación de conjuntos de carpetas de búsqueda personalizados  
 Puede definir un ámbito de búsqueda si hace clic en el botón **Elegir carpetas de búsqueda** (parecido a **...**) junto al cuadro **Buscar en**. En el cuadro de diálogo **Elegir carpetas de búsqueda**, puede especificar un conjunto de carpetas en el que buscar, y puede guardar la especificación para que pueda volver a usarla más tarde. Puede especificar carpetas de un equipo remoto solo si ha asignado su unidad al equipo local.  
  
### <a name="creating-custom-component-sets"></a>Creación de conjuntos de componentes personalizados  
 Puede definir conjuntos de componentes como su ámbito de búsqueda pulsando el botón **Editar conjunto de componentes personalizado** junto al cuadro **Buscar en**. Puede especificar componentes COM o .NET instalados, proyectos de Visual Studio que se incluyen en la solución o cualquier ensamblado o biblioteca de tipos (.dll, .tlb, .olb, .exe o .ocx). Para buscar referencias, seleccione el cuadro **Buscar en referencias**.  
  
## <a name="see-also"></a>Vea también  
 [Usar expresiones regulares en Visual Studio](../ide/using-regular-expressions-in-visual-studio.md)
