---
title: Crear un proyecto de prueba unitaria
ms.date: 01/29/2019
ms.topic: conceptual
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 381f04b78e5cfc9ed61187e62e310a2d927eb0ce
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "55949439"
---
# <a name="create-a-unit-test-project"></a>Crear un proyecto de prueba unitaria

Las pruebas unitarias a menudo reflejan la estructura del código sometido a pruebas. Por ejemplo, se crearía un proyecto de prueba unitaria para cada proyecto de código en el producto. El proyecto de prueba puede estar en la misma solución que el código de producción, o puede estar en una solución independiente. Puede tener varios proyectos de prueba unitaria en una solución.

> [!NOTE]
> La ubicación de las pruebas unitarias para código nativo y la estructura del proyecto de prueba puede ser diferente de la estructura que se describe en este artículo. Para obtener más información, vea [Writing unit tests for C/C++](writing-unit-tests-for-c-cpp.md) (Escritura de pruebas unitarias para C/C++).

## <a name="to-create-a-unit-test-project"></a>Para crear un proyecto de prueba unitaria

1. En el menú **Archivo**, elija **Nuevo** y después **Proyecto**. O bien, presione **Ctrl**+**Mayús**+**N**.

2. En el cuadro de diálogo **Nuevo proyecto**, expanda el nodo **Instalado**, elija el lenguaje que quiere usar para el proyecto de prueba y, después, elija **Probar**.

3. Para usar uno de los marcos de pruebas unitarias de Microsoft, elija **Proyecto de prueba unitaria** en la lista de plantillas de proyecto. De lo contrario, elija la plantilla de proyecto del marco de pruebas unitarias que desea usar. Asigne un nombre al proyecto y, después, haga clic en **Aceptar**.

4. En el proyecto de prueba unitaria, agregue una referencia al código en pruebas. Para agregar una referencia a un proyecto de código de la misma solución:

   1. Seleccione el proyecto en el **Explorador de soluciones**.

   2. En el menú **Proyecto** , elija **Agregar referencia**.

   3. En **Administrador de referencias**, haga clic en el nodo **Solución**, en **Proyectos**. Seleccione el proyecto de código que quiera probar y, después, haga clic en **Aceptar**.

   Si el código que quiere probar está en otra ubicación, vea [Administrar referencias en un proyecto](../ide/managing-references-in-a-project.md) para obtener información sobre cómo agregar una referencia.

## <a name="next-steps"></a>Pasos siguientes

Consulte una de las siguientes secciones:

**Escribir pruebas unitarias**

- [Haga una prueba unitaria de su código](../test/unit-test-your-code.md)

- [Escribir pruebas unitarias para C/C++](writing-unit-tests-for-c-cpp.md)

- [Usar el marco de trabajo MSTest en pruebas unitarias](using-microsoft-visualstudio-testtools-unittesting-members-in-unit-tests.md)

**Ejecutar pruebas unitarias**

- [Ejecutar pruebas unitarias con el Explorador de pruebas](../test/run-unit-tests-with-test-explorer.md)