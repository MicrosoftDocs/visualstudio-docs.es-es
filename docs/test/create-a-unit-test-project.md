---
title: Crear un proyecto de prueba unitaria en Visual Studio
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: d49748be3067ac2bbb6df9016883cb7be0f48f89
ms.sourcegitcommit: 56ae5032d99d948aae0548ae318ca2bae97ea962
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2018
ms.locfileid: "39586865"
---
# <a name="create-a-unit-test-project"></a>Crear un proyecto de prueba unitaria

Las pruebas unitarias a menudo reflejan la estructura del código sometido a pruebas. Por ejemplo, se crearía un proyecto de prueba unitaria para cada proyecto de código en el producto. El proyecto de prueba puede estar en la misma solución que el código de producción, o puede estar en una solución independiente. Puede tener varios proyectos de prueba unitaria en una solución.

> [!NOTE]
> La ubicación de las pruebas unitarias para código nativo y la estructura del proyecto de prueba puede ser diferente de la estructura que se describe en este tema. Para obtener más información, vea [Writing unit tests for C/C++](writing-unit-tests-for-c-cpp.md) (Escritura de pruebas unitarias para C/C++).

## <a name="to-create-a-unit-test-project"></a>Para crear un proyecto de prueba unitaria:

1.  En el menú **Archivo**, elija **Nuevo** y, después, **Proyecto** (teclado **Ctrl**+**Mayús**+**N**).

2.  En el cuadro de diálogo **Nuevo proyecto**, expanda el nodo **Instalado**, elija el lenguaje que quiere usar para el proyecto de prueba y, después, elija **Probar**.

3.  Para usar uno de los marcos de pruebas unitarias de Microsoft, elija **Proyecto de prueba unitaria** en la lista de plantillas de proyecto. De lo contrario, elija la plantilla de proyecto del marco de pruebas unitarias que desea usar. Para probar el proyecto Cuentas del ejemplo, el proyecto se denominaría **CuentasPrueba**.

4.  En el proyecto de prueba unitaria, agregue una referencia al código en pruebas.  Aquí se muestra cómo crear la referencia a un proyecto de código en la misma solución:

    1.  Seleccione el proyecto en el **Explorador de soluciones**.

    2.  En el menú **Proyecto** , elija **Agregar referencia**.

    3.  En el cuadro de diálogo **Administrador de referencias**, abra el nodo **Solución** y elija **Proyectos**. Compruebe el nombre del proyecto de código y cierre el cuadro de diálogo.

5.  Si el código que desea probar está en otra ubicación, consulte [Administrar referencias en un proyecto](../ide/managing-references-in-a-project.md) para obtener información sobre cómo agregar referencias.

## <a name="next-steps"></a>Pasos siguientes

 Consulte una de las siguientes secciones:

**Escribir pruebas unitarias**

- [Haga una prueba unitaria de su código](../test/unit-test-your-code.md)

- [Escribir pruebas unitarias para C/C++](writing-unit-tests-for-c-cpp.md)

- [Usar el marco de trabajo MSTest en pruebas unitarias](using-microsoft-visualstudio-testtools-unittesting-members-in-unit-tests.md)

**Ejecutar pruebas unitarias**

- [Ejecutar pruebas unitarias con el Explorador de pruebas](../test/run-unit-tests-with-test-explorer.md)