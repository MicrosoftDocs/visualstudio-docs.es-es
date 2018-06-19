---
title: Buscar y reemplazar texto
ms.date: 05/07/2018
ms.prod: visual-studio-dev15
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
- Find in Files dialog box
- text searches, finding and replacing text
- text, finding and replacing
- find and replace
- find text
- replace text
ms.assetid: a62545c3-1570-4d12-99fb-a82607eb35a1
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7051b90dde45965b76e8a9e08b33b5326ff2848c
ms.sourcegitcommit: 56018fb1f52f17bf35ae2ce71c50c763486e6173
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33106757"
---
# <a name="find-and-replace-text"></a>Buscar y reemplazar texto

Puede buscar y reemplazar texto en el editor de Visual Studio mediante [Buscar y reemplazar](#find-and-replace-control) o [Find/Replace in Files (Buscar/Reemplazar en archivos)](#find-in-files-and-replace-in-files).

> [!TIP]
> Si está cambiando el nombre de símbolos de código, como variables y métodos, es mejor que los *[refactorice](../ide/reference/rename.md)*  en lugar de usar Buscar y reemplazar. La refactorización es inteligente y entiende el ámbito, mientras que Buscar y reemplazar reemplaza de forma automática todas las instancias.

La funcionalidad Buscar y reemplazar está disponible en el editor, en otras ventanas basadas en texto como las ventanas **Resultados de la búsqueda**, en ventanas del diseñador, como el diseñador XAML y el diseñador de Windows Forms y en las ventanas de herramientas.

Puede definir el ámbito de las búsquedas en el documento actual, en la solución actual o en un conjunto personalizado de carpetas. También puede especificar un conjunto de extensiones de nombre de archivo para búsquedas de varios archivos. Personalice la sintaxis de búsqueda mediante [expresiones regulares](../ide/using-regular-expressions-in-visual-studio.md) .NET.

> [!TIP]
> El cuadro [Comando/Buscar](../ide/find-command-box.md) está disponible como un control de la barra de herramientas, pero no está visible de manera predeterminada. Para mostrar el cuadro **Comando/Buscar**, seleccione **Agregar o quitar botones** en la barra de herramientas **Estándar** y, después, seleccione **Buscar**.

## <a name="find-and-replace-control"></a>Control Buscar y reemplazar

El control **Buscar y reemplazar** aparece en la esquina superior derecha de la ventana del editor de código. El control **Buscar y reemplazar** resalta inmediatamente cada aparición de la cadena de búsqueda determinada en el documento actual. Puede ir de una aparición a otra pulsando el botón **Buscar siguiente** o en el botón **Buscar anterior** en el control de búsqueda.

![Control Buscar y reemplazar](media/find-and-replace-box.png)

Puede tener acceso a las opciones de reemplazo pulsando el botón siguiente al cuadro de texto **Buscar**. Para realizar un reemplazo puntual, pulse el botón **Reemplazar siguiente** junto al cuadro de texto **Reemplazar**. Para reemplazar todas las coincidencias, pulse el botón **Reemplazar todo**.

Para cambiar el color de resaltado de las coincidencias, pulse el menú **Herramientas**, seleccione **Opciones** y, después, pulse **Entorno** y **Fuentes y colores**. En la lista **Mostrar configuración para**, seleccione **Editor de texto** y, después, en la lista **Mostrar elementos**, seleccione **Buscar resaltado (Extensión)**.

### <a name="search-tool-windows"></a>Ventanas de herramientas de búsqueda

Puede usar el control **Buscar** en ventanas de texto o código, como ventanas de **Salida** y ventanas **Resultados de la búsqueda**, al seleccionar **Editar** > **Buscar y reemplazar** o presionando **CTRL+F**.

También está disponible una versión del control **Buscar** en algunas ventanas de herramientas. Por ejemplo, puede filtrar la lista de controles en la ventana **Cuadro de herramientas** escribiendo texto en el cuadro de búsqueda. Otras ventanas de herramientas que le permiten buscar su contenido incluyen **Explorador de soluciones**, la ventana **Propiedades** y **Team Explorer**.

## <a name="find-in-files-and-replace-in-files"></a>Buscar en archivos y reemplazar en archivos

**Buscar y reemplazar en archivos** funciona como el control **Buscar y reemplazar**, excepto que puede definir un ámbito para la búsqueda. No solo puede buscar el archivo abierto actual en el editor, sino que también todos los documentos abiertos, la solución completa, el proyecto actual y los conjuntos de carpetas seleccionados. También puede buscar mediante la extensión del nombre de archivo. Para tener acceso al cuadro de diálogo **Buscar y reemplazar en archivos**, seleccione **Buscar y reemplazar** en el menú **Edición** o presione **Ctrl+Mayús+F**.

![Buscar en archivos (cuadro de diálogo)](media/find-in-files-box.png)

### <a name="find-results"></a>Resultados de la búsqueda

Cuando pulse **Buscar todo**, se abre una ventana **Buscar resultados** y se muestran las coincidencias de la búsqueda. Al seleccionar un resultado en la lista se muestra el archivo asociado y se resalta la coincidencia. Si el archivo todavía no está abierto para su edición, se abre en una pestaña de vista previa en el lateral derecho de la pestaña también. Puede usar el control **Buscar** para buscar en la lista **Resultados de la búsqueda**.

### <a name="create-custom-search-folder-sets"></a>Crear conjuntos de carpetas de búsqueda personalizados

Puede definir un ámbito de búsqueda pulsando el botón **Elegir carpetas de búsqueda** (parecido a **...**) junto al cuadro **Buscar en**. En el cuadro de diálogo **Elegir carpetas de búsqueda**, puede especificar un conjunto de carpetas en el que buscar, y puede guardar la especificación para que pueda volver a usarla más tarde.

> [!TIP]
> Si ha asignado la unidad de un equipo remoto al equipo local, puede especificar las carpetas que se van a buscar en el equipo remoto.

### <a name="create-custom-component-sets"></a>Crear conjuntos de componentes personalizados

Puede definir conjuntos de componentes como su ámbito de búsqueda pulsando el botón **Editar conjunto de componentes personalizado** junto al cuadro **Buscar en**. Puede especificar componentes COM o .NET instalados, proyectos de Visual Studio que se incluyen en la solución o cualquier ensamblado o biblioteca de tipos (*.dll*, *.tlb*, *.olb*, *.exe* u *.ocx*). Para buscar referencias, seleccione el cuadro **Buscar en referencias**.

## <a name="see-also"></a>Vea también

- [Usar expresiones regulares en Visual Studio](../ide/using-regular-expressions-in-visual-studio.md)
- [Refactorizar el código en Visual Studio](../ide/refactoring-in-visual-studio.md)