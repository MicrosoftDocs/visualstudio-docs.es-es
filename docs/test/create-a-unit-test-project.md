---
title: Crear un proyecto de prueba unitaria
description: Aprenda a crear un proyecto de prueba unitaria. El proyecto de prueba puede estar en la misma solución que el código de producción, o puede estar en una solución independiente.
ms.custom: SEO-VS-2020
ms.date: 01/29/2019
ms.topic: how-to
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 8ca3cbe82bf4253e660ce69960570e40702c5512
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99942365"
---
# <a name="create-a-unit-test-project"></a>Crear un proyecto de prueba unitaria

Las pruebas unitarias a menudo reflejan la estructura del código sometido a pruebas. Por ejemplo, se crearía un proyecto de prueba unitaria para cada proyecto de código en el producto. El proyecto de prueba puede estar en la misma solución que el código de producción, o puede estar en una solución independiente. Puede tener varios proyectos de prueba unitaria en una solución.

> [!NOTE]
> La ubicación de las pruebas unitarias para código nativo y la estructura del proyecto de prueba puede ser diferente de la estructura que se describe en este artículo. Para obtener más información, vea [Writing unit tests for C/C++](writing-unit-tests-for-c-cpp.md) (Escritura de pruebas unitarias para C/C++).

## <a name="to-create-a-unit-test-project"></a>Para crear un proyecto de prueba unitaria

1. En el menú **Archivo**, elija **Nuevo** > **Proyecto** o presiones **Ctrl**+**Mayús**+**N**.

::: moniker range="vs-2017"

2. En el cuadro de diálogo **Nuevo proyecto**, expanda el nodo **Instalado**, elija el lenguaje que quiere usar para el proyecto de prueba y, después, elija **Probar**.

3. Seleccione la plantilla de proyecto del marco de pruebas que desea usar, por ejemplo, **Proyecto de prueba de MSTest** o **Proyecto de prueba de NUnit**. Asigne un nombre al proyecto y, después, elija **Aceptar**.

   ![Plantillas de proyecto de prueba de Visual Studio 2017](media/test-project-templates.png)

::: moniker-end

::: moniker range=">=vs-2019"

2. En el cuadro de búsqueda de la página **Crear un proyecto**, escriba **prueba unitaria**. Seleccione la plantilla de proyecto del marco de pruebas que desea usar, por ejemplo, **Proyecto de prueba de MSTest** o **Proyecto de prueba de NUnit** y, luego, elija **Siguiente**.

   ![Plantillas de proyecto de prueba de Visual Studio 2019](media/vs-2019/test-project-templates.png)

3. En la página **Configurar el nuevo proyecto**, escriba un nombre para el proyecto y elija **Crear**.

::: moniker-end

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
