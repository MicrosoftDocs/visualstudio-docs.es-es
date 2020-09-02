---
title: Características del shell del Diseñador de flujo de trabajo
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- WFDShellFeatures.UI
ms.assetid: 14bfe312-9592-408e-92ce-e98585ad16e7
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5a6b192eae3340c6a3d84bb3ccbcce7cbf8d65b3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85816389"
---
# <a name="workflow-designer-shell-features"></a>Características del shell del Diseñador de flujo de trabajo

Diseñador de flujo de trabajo se compone de tres áreas principales de la interfaz de usuario: la superficie del diseñador, la barra de ruta de navegación que está por encima y el shell debajo. La barra de ruta de navegación, que se encuentra en la parte superior de la pantalla, se utiliza para mostrar la lista de antecesores de la actividad raíz actual. Para obtener más información, consulte [Cómo: usar la navegación por la ruta](../workflow-designer/how-to-use-breadcrumb-navigation.md)de navegación. La superficie del diseñador, que se encuentra en el centro de la pantalla, se utiliza para crear los flujos de trabajo. El shell, que se encuentra en la parte inferior de la pantalla, contiene diversos botones para administrar la vista actual.

## <a name="shell-features"></a>Características del shell
 El shell tiene botones a la derecha de la barra que puede utilizar para acercar o alejar el flujo de trabajo, ajustar el contenido del flujo de trabajo según el tamaño de la pantalla y mostrar u ocultar el mapa general. También puede acercar o alejar un flujo de trabajo con los métodos abreviados de teclado CTRL++ y CTRL+ -.

## <a name="overview-map"></a>Mapa general
 El mapa general muestra una versión reducida de la totalidad de la actividad en la raíz de la ruta de navegación actual, incluso todos sus elementos secundarios y los expandidos. Hay una ventanilla, un rectángulo con un borde naranja, que resalta la parte de la actividad que se muestra en esos momentos en el editor. Si se arrastra el rectángulo en torno al mapa general, se desplaza el diseñador de flujos de trabajo y cambia la vista del editor.

> [!NOTE]
> La interfaz de usuario Diseñador de flujo de trabajo está virtualizada. Los diseñadores de actividades se presentan solo cuando se requieran. Si una parte del flujo de trabajo no se ha dibujado nunca en la superficie del diseñador, esa parte aparecerá en blanco en el mapa general. Al desplazarse por el mapa general, se dibuja enteramente el flujo de trabajo.

## <a name="copying-or-saving-workflows-as-images"></a>Copiar o guardar flujos de trabajo como imágenes
 Los flujos de trabajo se pueden copiar en formato de mapa de bits o guardar en formato de mapa de bits o de vector. Copiar o guardar una imagen ofrece una forma de exportar a otro programa una vista de la totalidad de la actividad en la raíz de la ruta de navegación actual, lo cual incluye todos sus elementos secundarios y los expandidos.

 Para copiar como imagen, haga clic con el botón secundario en cualquier lugar del diseñador y seleccione **Copiar como imagen**. Para guardar como imagen, haga clic con el botón derecho en cualquier parte del diseñador y seleccione **Guardar como imagen**. Los flujos de trabajo pueden guardarse en formato JPG, PNG, GIF o XPS. El formato se selecciona en el cuadro de diálogo **Guardar como** en el cuadro de lista desplegable **Guardar como tipo:** situado en la parte inferior de la ventana.

## <a name="fonts-and-colors"></a>Fuentes y colores

Las fuentes que se usan en Diseñador de flujo de trabajo dentro de Visual Studio se controlan mediante la fuente del entorno. Los colores que se muestran en Diseñador de flujo de trabajo cambian si usa una combinación de colores de contraste alto para el tema del sistema operativo. Debe reiniciar Visual Studio después de realizar un cambio en la configuración de fuente o de color antes de que los cambios surtan efecto en Diseñador de flujo de trabajo.