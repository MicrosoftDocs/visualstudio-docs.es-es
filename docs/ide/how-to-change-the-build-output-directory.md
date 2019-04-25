---
title: Filtrar Cambiar el directorio de salida de compilación
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- output directory, changing
ms.assetid: a8333c89-afb2-4b1d-b2e2-9146da852402
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2f254c29f2951484869b814f13d1a346080fab07
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "55911538"
---
# <a name="how-to-change-the-build-output-directory"></a>Filtrar Cambiar el directorio de salida de compilación

Puede especificar la ubicación de salida por configuración (para debug, release o ambos) generada por el proyecto.

> [!NOTE]
> Si tiene un proyecto **Setup**, vea la nota que se proporciona al final de este artículo.

## <a name="change-the-build-output-directory"></a>Cambiar el directorio de salida de compilación

1.  En la barra de menús, elija **Proyecto** > **\<NombreDeAplicación>Propiedades**. En el **Explorador de soluciones**, también puede hacer clic con el botón derecho en el nodo del proyecto y seleccionar **Propiedades**.

2.  Si tiene un proyecto de Visual Basic, seleccione la pestaña **Compilar** . Si tiene un proyecto de C#, seleccione la pestaña **Compilar**. Si tiene un proyecto de C++ o JavaScript, seleccione la pestaña **General** .

3.  En la lista desplegable de configuración de la parte superior, elija la configuración cuya ubicación de archivo de resultados desea cambiar (debug, release o todas).

     Busque la entrada de la ruta de acceso de la salida (**Ruta de acceso de salida de la compilación** en Visual Basic, **Directorio de salida** en Visual C++ y **Ruta de acceso de salida** en JavaScript y C#). Especifique un nuevo directorio de resultados de la compilación relativo al directorio del proyecto.

> [!NOTE]
> En un proyecto Setup, el cuadro **Nombre del archivo de salida** cambia solo la ubicación del archivo *Setup.exe*, no la ubicación de los archivos del proyecto. Para obtener más información, vea **Compilación, Propiedades de configuración, Propiedades del proyecto de implementación (cuadro de diálogo)**.

## <a name="see-also"></a>Vea también

- [Página Compilar, Diseñador de proyectos (C#)](../ide/reference/build-page-project-designer-csharp.md)
- [Página Propiedad general (Proyecto)](/cpp/ide/general-property-page-project)
- [Compilar y generar](../ide/compiling-and-building-in-visual-studio.md)