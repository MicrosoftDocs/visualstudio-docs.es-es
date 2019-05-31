---
title: Ir a archivo, ir a símbolo, ir a línea
ms.date: 08/14/2018
ms.topic: conceptual
helpviewer_keywords:
- code editor, go to
- code editor, go to line
- go to line
- go to
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 588bc57dc2cda1030e9e1b8d1f989b2cc2d31662
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62550066"
---
# <a name="find-code-using-go-to-commands"></a>Buscar código mediante comandos Ir a

Los comandos **Ir a** de Visual Studio realizan una búsqueda centrada en su código para ayudarle a encontrar rápidamente elementos específicos. Puede ir a una línea, tipo, símbolo, archivo o miembro específicos desde una interfaz sencilla y unificada.

## <a name="how-to-use-it"></a>Cómo se usa

Entrada | Función
------------ | ---
**Teclado** | Presione **Ctrl**+**T** o **Ctrl**+ **,**
**Mouse** | Seleccione **Editar** > **Ir a** > **Ir a Todo**

Aparecerá una pequeña ventana en la parte superior derecha del editor de código.

![Ventana Ir a todo](media/go-to-all.png)

A medida que escribe en el cuadro de texto, los resultados aparecen en una lista desplegable debajo del cuadro de texto. Para ir a un elemento, púlselo en la lista.

![Ventana Navegar a](../ide/media/vside_navigatetowindow.png)

También puede escribir un signo de interrogación ( **?** ) para obtener ayuda adicional.

![Ayuda de Ir a todo](media/go-to-all-help.png)

## <a name="filtered-searches"></a>Búsquedas filtradas

De forma predeterminada, el elemento especificado se busca en todos los elementos de la solución, pero puede limitar la búsqueda de código a tipos de elemento específicos si coloca determinados caracteres delante de los términos de búsqueda. Además, puede cambiar rápidamente el filtro de búsqueda si selecciona los botones de la barra de herramientas del cuadro de diálogo **Ir a**. Los botones que cambian los filtros de tipo se encuentran a la izquierda y los botones que cambian el ámbito de la búsqueda se encuentran a la derecha.

![Ir a miembros](../ide/media/vside_navigation_toolbar.png)

### <a name="filter-to-a-specific-type-of-code-element"></a>Filtrar por un tipo específico de elemento de código

Para limitar la búsqueda a un tipo específico de elemento de código, puede especificar un prefijo en el cuadro de búsqueda o seleccionar uno de los cinco iconos de filtro:

Prefijo | Iconos | Acceso directo | Descripción
:-: | - | - | -
:| ![Icono de línea](media/gotoall-line-icon.png) | **Ctrl**+**G** | Ir al número de línea especificado
f| ![Icono de archivos](media/gotoall-files-icon.png) | **Ctrl**+**1**, **Ctrl**+**F** | Ir al archivo especificado
r| ![Icono de archivos recientes](media/gotoall-recent-files-icon.png) | **Ctrl**+**1**, **Ctrl**+**R** | Ir al archivo especificado que haya visitado recientemente
m| ![Icono de tipos](media/gotoall-types-icon.png) | **Ctrl**+**1**, **Ctrl**+**T** | Ir al tipo especificado
m| ![Icono de miembros](media/gotoall-members-icon.png) | **Ctrl**+**1**, **Ctrl**+**M** | Ir al miembro especificado
\#| ![Icono de símbolos](media/gotoall-symbols-icon.png) | **Ctrl**+**1**, **Ctrl**+**S** | Ir al símbolo especificado

### <a name="filter-to-a-specific-location"></a>Filtrar en una ubicación específica

Para restringir la búsqueda a una ubicación específica, use uno de los dos iconos de documento:

Iconos | Descripción
---- | ---
![Documento actual](media/gotoall_currentdocument.png) | Buscar solo en el documento actual
![Documentos externos](media/gotoall_external.png) | Buscar en documentos externos y en los que se encuentran en el proyecto o solución

## <a name="camel-casing"></a>Grafía Camel

Si usa la [grafía Camel](https://en.wikipedia.org/wiki/Camel_case) en el código, puede buscar elementos de código más rápido al escribir solo las letras en mayúscula del nombre del elemento de código. Por ejemplo, si el código tiene un tipo denominado `CredentialViewModel`, puede limitar la búsqueda si selecciona el filtro **Tipo** (**t**) y escribe solo las letras mayúsculas del nombre (`CVM`) en el cuadro de diálogo Ir a. Esta característica es útil si el código tiene nombres largos.

![Ventana Navegar a: buscar con mayúsculas](../ide/media/vside_capitalsearch.png)

## <a name="settings"></a>Configuración

Si selecciona el icono de engranaje ![Icono de engranaje](media/gotoall_gear.png) puede cambiar el funcionamiento de esta característica:

Parámetro | Descripción
------- | ---
Usar pestaña de vista previa | Mostrar el elemento seleccionado inmediatamente en la pestaña de vista previa del IDE
Mostrar detalles | Mostrar la información de proyecto, archivo, línea y resumen de los comentarios de documentación en la ventana
Centrar ventana | Mover esta ventana a la parte superior central del editor de código, en lugar de a la parte superior derecha

## <a name="see-also"></a>Vea también

- [Navegación en el código](../ide/navigating-code.md)
- [Cuadro de diálogo Ir a la línea](../ide/reference/go-to-line.md)
- [Ir a definición y Ver la definición](../ide/go-to-and-peek-definition.md)