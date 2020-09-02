---
title: Visualización de datos de muestra en una interfaz de usuario de XAML
titleSuffix: Blend for Visual Studio
ms.date: 03/06/2018
ms.topic: conceptual
ms.assetid: 87d31b6c-4607-4121-bb7d-cfc80390ab93
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bd48ac8f5753521240ed3feb6003d945786820a3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85329093"
---
# <a name="display-data-in-blend-for-visual-studio"></a>Visualización de datos en Blend para Visual Studio

Mientras personaliza el diseño de sus páginas, puede ver datos de ejemplo en el diseñador. Estos datos de ejemplo se pueden generar desde cero o mediante una clase existente. También puede conectarse a *Datos en directo* que aparecen en la aplicación al ejecutarla.

> [!NOTE]
> El panel **datos** de Blend solo se admite para los proyectos que tienen como destino .NET Framework. No se admite para proyectos o proyectos de UWP que tengan como destino .NET Core.

## <a name="generate-sample-data"></a>Generación de datos de ejemplo

Para generar datos de ejemplo, abra un documento XAML. En el panel **Datos**, elija el botón **Crear datos de ejemplo** ![Icono Crear datos de ejemplo](../designers/media/30540d76-7256-43ce-b5d9-4b2edf3d339f.png) y, después, elija **Nuevos datos de ejemplo**.

Defina la estructura de los datos en el panel **Datos** y, a continuación, enlácelos a los elementos de interfaz de usuario de cualquier página.

![Panel de datos](../designers/media/496d7ebc-fe46-42f6-95a8-57b0e5be5d49.png)

Si desea que los datos de ejemplo aparezcan en las páginas al ejecutar la aplicación, elija **Opciones de origen de datos** ![Icono Opciones de origen de datos](../designers/media/ae1fd260-4f84-420d-b196-45fde357d81d.png) y, a continuación, **Habilitar al ejecutar la aplicación**.

![Elemento de menú Habilitar al ejecutar la aplicación](../designers/media/05d5356d-91bb-4e6b-b3f7-29b76852c4b3.png)

**Vea un vídeo corto:** ![Icono de reproducción](../designers/media/bldadminconsoleinitialconfigicon.PNG) [Crear datos de ejemplo desde cero](https://www.bing.com/videos/search?q=blend%20data&qs=n&form=QBVR&pq=blend%20data&sc=8-7&sp=-1&sk=#view=detail&mid=F8F2449A76956D480FD2F8F2449A76956D480FD2).

## <a name="generate-sample-data-from-a-class"></a>Generar datos de ejemplo desde una clase

Si ya ha creado las clases que describen la estructura de los datos, puede generar datos de ejemplo a partir de ellas.

Para generar datos de ejemplo desde una clase, abra un documento XAML y, en el panel **Datos**, haga clic en el botón **Crear datos de ejemplo** ![Icono Crear datos de ejemplo](../designers/media/30540d76-7256-43ce-b5d9-4b2edf3d339f.png) y, después, haga clic en **Crear datos de ejemplo desde clase**.

**Vea un vídeo corto:** ![Icono de reproducción](../designers/media/bldadminconsoleinitialconfigicon.PNG) [Mezclar algunos enlaces de datos con Blend](https://www.youtube.com/watch?v=LSwPB6CAvjg).

## <a name="see-also"></a>Vea también

- [Creación de una interfaz de usuario con Blend para Visual Studio](../xaml-tools/creating-a-ui-by-using-blend-for-visual-studio.md)
