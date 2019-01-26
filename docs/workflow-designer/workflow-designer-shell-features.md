---
title: Características del shell del Diseñador de flujo de trabajo
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
f1_keywords:
- WFDShellFeatures.UI
ms.assetid: 14bfe312-9592-408e-92ce-e98585ad16e7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 538a9d7b0a895b5cc50c04c107dad55d1c662f3f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54977517"
---
# <a name="workflow-designer-shell-features"></a>Características del shell del Diseñador de flujo de trabajo

Diseñador de flujo de trabajo se compone de tres áreas principales de la interfaz de usuario: la superficie del diseñador, la barra de ruta de navegación por encima de él y el shell debajo de él. La barra de ruta de navegación, que se encuentra en la parte superior de la pantalla, se utiliza para mostrar la lista de antecesores de la actividad raíz actual. Para obtener más información, vea [Cómo: Usar ruta de navegación](../workflow-designer/how-to-use-breadcrumb-navigation.md). La superficie del diseñador, que se encuentra en el centro de la pantalla, se utiliza para crear los flujos de trabajo. El shell, que se encuentra en la parte inferior de la pantalla, contiene diversos botones para administrar la vista actual.

## <a name="shell-features"></a>Características del shell
 El shell tiene botones a la derecha de la barra que puede utilizar para acercar o alejar el flujo de trabajo, ajustar el contenido del flujo de trabajo según el tamaño de la pantalla y mostrar u ocultar el mapa general. También puede acercar o alejar un flujo de trabajo con los métodos abreviados de teclado CTRL++ y CTRL+ -.

## <a name="overview-map"></a>Mapa general
 El mapa general muestra una versión reducida de la totalidad de la actividad en la raíz de la ruta de navegación actual, incluso todos sus elementos secundarios y los expandidos. Hay una ventanilla, un rectángulo con un borde naranja, que resalta la parte de la actividad que se muestra en esos momentos en el editor. Si se arrastra el rectángulo en torno al mapa general, se desplaza el diseñador de flujos de trabajo y cambia la vista del editor.

> [!NOTE]
> La interfaz de usuario del Diseñador de flujo de trabajo está virtualizada. Los diseñadores de actividades se presentan solo cuando se requieran. Si una parte del flujo de trabajo no se ha dibujado nunca en la superficie del diseñador, esa parte aparecerá en blanco en el mapa general. Al desplazarse por el mapa general, se dibuja enteramente el flujo de trabajo.

## <a name="copying-or-saving-workflows-as-images"></a>Copiar o guardar flujos de trabajo como imágenes
 Los flujos de trabajo se pueden copiar en formato de mapa de bits o guardar en formato de mapa de bits o de vector. Copiar o guardar una imagen ofrece una forma de exportar a otro programa una vista de la totalidad de la actividad en la raíz de la ruta de navegación actual, lo cual incluye todos sus elementos secundarios y los expandidos.

 Para copiar como imagen, haga clic en cualquier lugar en el diseñador y seleccione **copiar como imagen**. Para guardar como imagen, haga clic en cualquier lugar en el diseñador y seleccione **Guardar como imagen**. Los flujos de trabajo pueden guardarse en formato JPG, PNG, GIF o XPS. El formato seleccionado en el **Guardar como** cuadro de diálogo en el **Guardar como tipo:** cuadro de lista en la parte inferior de la ventana de lista desplegable.

## <a name="fonts-and-colors"></a>Fuentes y colores

Las fuentes usadas en el Diseñador de flujo de trabajo dentro de Visual Studio están controladas por la fuente del entorno. Los colores mostrada en el Diseñador de flujo de trabajo cambian si usa una combinación de colores de contraste alto para el tema del sistema operativo. Debe reiniciar Visual Studio después de realizar un cambio en la configuración de fuente o color para que los cambios surtan efecto en el Diseñador de flujo de trabajo.