---
title: Instalar marcos de prueba unitaria de terceros
ms.date: 04/01/2019
ms.topic: conceptual
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: b70e26adc7c0c9a8dc409d9b4b971b233418b8e1
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75594284"
---
# <a name="install-unit-test-frameworks"></a>Instalación de marcos de pruebas unitarias

El Explorador de pruebas de Visual Studio puede ejecutar pruebas de cualquier marco de pruebas unitarias que haya desarrollado una interfaz de adaptador para él. El programa instalación del marco copia los archivos binarios y agrega plantillas del proyecto de Visual Studio para los idiomas que admite. Cuando crea un proyecto con la plantilla, el marco se registra en el Explorador de pruebas.

Una solución de Visual Studio puede contener proyectos de prueba unitaria que usen diferentes marcos y que estén destinados a diferentes idiomas.

[MSTest](getting-started-with-unit-testing.md) es el marco de pruebas que ofrece Visual Studio y está instalado de forma predeterminada.

## <a name="acquire-frameworks"></a>Adquisición de marcos de trabajo

Instale marcos de pruebas unitarias de terceros mediante **Administrador de paquetes NuGet**.

1. Haga clic con el botón derecho en el proyecto que va a contener el código de prueba y seleccione **Administrar paquetes NuGet**.

2. En el **Administrador de paquetes NuGet**, busque el marco de pruebas que quiera instalar y haga clic en **Instalar**.

   ![Administrador de paquetes NuGet en Visual Studio](media/vs-2019/nuget-package-manager.png)

## <a name="update-to-the-latest-test-adapters"></a>Actualización a los adaptadores de prueba más recientes

Actualice al adaptador de pruebas estable más reciente para experimentar una mejor ejecución y detección de pruebas. Para obtener más información acerca de las actualizaciones de MSTest, NUnit y los adaptadores de prueba de xUnit, consulte el [blog de Visual Studio](https://devblogs.microsoft.com/visualstudio/test-experience-improvements/).

### <a name="to-update-to-the-latest-stable-test-adapter-version"></a>Para actualizar a la versión de adaptador de prueba estable más reciente

1. Abra el Administrador de paquetes de NuGet de la solución; para ello, vaya a **Herramientas** > **Administrador de paquetes de NuGet** > **Administrar paquetes de NuGet para la solución**.

2. Haga clic en la pestaña **Actualizaciones** y busque los adaptadores de prueba MSTest, NUnit o xUnit instalados.

3. Seleccione cada adaptador de prueba y, después, seleccione la versión estable más reciente en el menú desplegable.

4. Seleccione el botón **Instalar**.

   ![Actualización del adaptador de prueba](media/install-adapter-upgrade.png)

## <a name="see-also"></a>Vea también

- [Haga una prueba unitaria de su código](../test/unit-test-your-code.md)
