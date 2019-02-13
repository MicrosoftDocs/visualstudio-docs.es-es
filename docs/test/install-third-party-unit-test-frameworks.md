---
title: Instalar marcos de prueba unitaria de terceros
ms.date: 06/07/2018
ms.topic: conceptual
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: b4dd4e347d6a8c96cef9ce9028071214200682c4
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "55916172"
---
# <a name="install-unit-test-frameworks"></a>Instalación de marcos de pruebas unitarias

El Explorador de pruebas de Visual Studio puede ejecutar cualquier marco de pruebas que haya desarrollado una interfaz de adaptador para el explorador. El programa de instalación del marco instala los binarios y agrega plantillas del proyecto de Visual Studio para los idiomas que admite. Cuando crea un proyecto con la plantilla, el marco se registra en el Explorador de pruebas. Una solución de Visual Studio puede contener proyectos de prueba unitaria que usen diferentes marcos y que estén destinados a diferentes idiomas. El Explorador de pruebas los ejecuta todos.

[MSTest](getting-started-with-unit-testing.md) es el marco de pruebas proporcionado por Visual Studio y se instala con Visual Studio de forma predeterminada.

## <a name="acquire-frameworks"></a>Adquisición de marcos de trabajo

Puede descargar e instalar marcos de pruebas unitarias de terceros mediante el Administrador de extensiones de Visual Studio o desde [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs). Los marcos también pueden descargarse desde otros sitios, como el sitio web del marco.

### <a name="install-from-visual-studio"></a>Instalar desde Visual Studio

1. En el menú estándar, seleccione **Herramientas** y **Extensiones y actualizaciones**.

2. Expanda **En línea** > **Visual Studio Marketplace** > **Herramientas**. Seleccione **Pruebas**.

3. Examine la lista para buscar el marco.

4. Elija el marco y seleccione **Descargar**.

Para obtener más información, vea [Buscar y usar extensiones de Visual Studio](../ide/finding-and-using-visual-studio-extensions.md).

### <a name="install-from-the-web"></a>Instalar desde Internet

Si sabe qué marco le interesa, realice lo siguiente:

1. Abra [Visual Studio Marketplace ](https://marketplace.visualstudio.com/vs).

2. Escriba el nombre del marco en el cuadro **Buscar**.

3. Elija el marco en la lista de resultados para desplazarse a la página de **Visual Studio Marketplace** de la herramienta.

Para examinar una lista de los marcos junto con otras herramientas de pruebas, realice lo siguiente:

1. Abra [Visual Studio Marketplace ](https://marketplace.visualstudio.com/vs).

2. En **Filtrar por categoría/colección**, elija **Ver todo**.

3. En la lista **Categoría** (etiquetada como **Mostrando**), expanda el nodo **Herramientas** y seleccione **Pruebas**.

4. Elija un marco en la lista de resultados para desplazarse a la página de **Visual Studio Marketplace** de la herramienta.

## <a name="update-to-the-latest-test-adapters"></a>Actualización a los adaptadores de prueba más recientes

Actualice al adaptador de pruebas estable más reciente para experimentar una mejor ejecución y detección de pruebas. Para obtener más información acerca de las actualizaciones de MSTest, NUnit y los adaptadores de prueba de xUnit, consulte el [blog de Visual Studio](https://blogs.msdn.microsoft.com/visualstudio/2017/11/16/test-experience-improvements/).

### <a name="to-update-to-the-latest-stable-test-adapter-version"></a>Para actualizar a la versión de adaptador de prueba estable más reciente

1. Abra el Administrador de paquetes de NuGet de la solución; para ello, vaya a **Herramientas** > **Administrador de paquetes de NuGet** > **Administrar paquetes de NuGet para la solución**.

2. Haga clic en la pestaña **Actualizaciones** y busque los adaptadores de prueba MSTest, NUnit o xUnit instalados.

3. Seleccione cada adaptador de prueba y, después, seleccione la versión estable más reciente en el menú desplegable.

4. Seleccione el botón **Instalar**.

   ![Actualización del adaptador de prueba](media/install-adapter-upgrade.png)

## <a name="see-also"></a>Vea también

- [Haga una prueba unitaria de su código](../test/unit-test-your-code.md)
