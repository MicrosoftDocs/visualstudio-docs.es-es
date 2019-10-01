---
title: Prueba unitaria de una aplicación en contenedores
author: ghogen
description: Ejecute pruebas unitarias con cada compilación para un proyecto de Docker en Visual Studio
ms.author: ghogen
ms.date: 06/17/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: ec5aea44362cf82f6745671cc0706f80e01a60ad
ms.sourcegitcommit: 0cd282a7584b9bfd4df7882f8fdf3ad8a270e219
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/28/2019
ms.locfileid: "71125972"
---
# <a name="how-to-run-unit-tests-for-a-containerized-app"></a>Procedimiento Ejecutar pruebas unitarias para una aplicación en contenedores

Puede modificar su Dockerfile para ejecutar pruebas unitarias con cada compilación de su proyecto en contenedores.

## <a name="prerequisites"></a>Requisitos previos

- [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
- Instalación de [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)
- Pruebas unitarias configuradas para ejecutarse con [pruebas de dotnet](/dotnet/core/tools/dotnet-test)
- Instalación de la [extensión de la ventana Containers](https://aka.ms/vscontainerspreview)

## <a name="add-unit-tests-to-the-dockerfile"></a>Adición de pruebas unitarias Dockerfile

Visual Studio realiza algunas optimizaciones de rendimiento especiales antes de modificar el Dockerfile. Al compilar la configuración **Debug**, Visual Studio compila los proyectos en el equipo local y copia los resultados en el contenedor. Por lo tanto, solo se ejecuta la primera fase de varias de Dockerfile, tal como se especifica en Dockerfile. Para obtener más información, consulte [Proceso de compilación de herramientas de contenedor para Visual Studio](container-build.md).

Para agregar pruebas unitarias a un Dockerfile de varias fases, agregue una fase `unit-test` a Dockerfile entre las fases `build` y `publish`.

```
FROM build AS unit-test
RUN dotnet unit-test --logger:trx
```

Visual Studio solo ejecuta la primera fase en la configuración **Debug**, por lo que la fase `unit-test` solo se ejecuta en la configuración **Release**. Pero incluso en la configuración **Release**, los resultados del registro no se incluirán en la imagen final, porque la imagen final se compila a partir de la fase `base` y no de la fase `unit-test`. Para ejecutar las pruebas y generar una imagen en la que pueda ver los registros, use el siguiente comando:

```cmd
docker build --target:unit-test
```

## <a name="next-steps"></a>Pasos siguientes

A continuación, puede usar la ventana [Containers](view-and-diagnose-containers.md) (si tiene la extensión instalada) para ver los registros de prueba.  

Para ver los registros de prueba, use **Ctrl**+**Q** y busque **Containers** para abrir la ventana **Containers**. En la ventana **Containers**, busque el contenedor, abra la pestaña **Files**, busque el archivo de los resultados de pruebas (.trx) en el sistema de archivos del contenedor y ábralo para ver los resultados en Visual Studio.

