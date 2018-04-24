---
title: Página de opciones del Diseñador XAML
ms.date: 03/02/2017
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.XAMLDesigner
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: 045f9105abd9fe52e9496adb9ba6d1a434bf9b90
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
---
# <a name="xaml-designer-options-page"></a>Página de opciones del Diseñador XAML

Use la página de opciones del **Diseñador XAML** para especificar cómo se aplica formato a los elementos y atributos en los documentos XAML. Para abrir esta página, seleccione pulse el menú **Herramientas** y, después, elija **Opciones**. Para tener acceso a la página de propiedades **Diseñador XAML**, pulse el nodo **Diseñador XAML**. La configuración para el diseñador XAML se aplica cuando abre el documento. De esta manera, si realiza cambios en la configuración, necesita cerrar y volver a abrir Visual Studio para ver los cambios.

> [!NOTE]
> Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas** . Para más información, vea [Personalizar el IDE de Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="enable-xaml-designer"></a>Habilitar el diseñador XAML

Cuando se selecciona, esta configuración habilita el diseñador XAML. El diseñador XAML proporciona un área de trabajo visual para que edite los documentos XAML. Determinadas funciones de Visual Studio, como IntelliSense para recursos y enlace de datos, requieren que el diseñador XAML esté habilitado.

La siguiente configuración se aplica solo cuando el diseñador XAML está habilitado. Si cambia esta opción, necesitará reiniciar Visual Studio para que la configuración surta efecto.

## <a name="default-document-view"></a>Vista de documento predeterminada

Use esta configuración para controlar si la vista de diseño aparece al cargar documentos XAML.

|||
|-|-|
|**Vista Código fuente**|Especifica si solo el código fuente XAML aparece en la vista XAML. Esto es útil al cargar documentos grandes.|
|**Vista de diseño**|Especifica si solo aparece un diseñador XAML visual en la vista XAML.|
|**Vista en dos paneles**|Especifica si el diseñador XAML visual y el código fuente XAML aparecen juntos en la vista XAML (la ubicación se basa en la configuración de **Orientación dividida**).|

## <a name="split-orientation"></a>Orientación dividida

Use esta configuración para controlar cuándo y cómo aparece el diseñador XAML al editar un documento XAML. Esta configuración se aplica solo cuando **Vista de documentos predeterminada** está establecida en **Vista en dos paneles**.

|||
|-|-|
|**Vertical**|El código fuente XAML aparece en el lateral izquierdo de la vista XAML, mientras que el diseñador XAML aparece en el otro lado.|
|**Horizontal**|El diseñador XAML aparece en la parte superior de la vista XAML y el código fuente XAML aparece debajo.|
|**Predetermiado**|El documento XAML usa la orientación dividida recomendada para la plataforma de destino del proyecto del documento. Para la mayoría de las plataformas esto equivale a **Horizontal**.|

## <a name="zoom-by-using"></a>Zoom mediante

Use esta configuración para determinar cómo funciona el zoom al editar un documento XAML.

|||
|-|-|
|**Rueda del mouse**|Acerque el diseñador XAML desplazando la rueda del mouse.|
|**Ctrl + rueda del mouse**|Acerque el diseñador XAML presionando la tecla CTRL mientras desplaza la rueda del mouse.|
|**Alt + rueda del mouse**|Acerque el diseñador XAML presionando la tecla ALT mientras desplaza la rueda del mouse.|

Esta configuración determina el comportamiento del diseñador al editar un documento XAML.

|||
|-|-|
|**Asignar nombre automáticamente a los elementos interactivos cuando se creen**|Especifica si se proporciona un nombre predeterminado para un nuevo elemento interactivo cuando agrega uno al diseñador.|
|**Insertar automáticamente las propiedades de diseño en la creación del elemento**|Especifica si se proporcionan propiedades de diseño para un nuevo elemento cuando agrega uno al diseñador.|
|**Usar diseño basado en cuadrantes**|Especifica si el control seleccionado actualmente se alinea con los bordes más cercanos del contenedor primario. Si esta casilla está desactivada, las alineaciones del control no cambian durante una operación de creación o movimiento.|
|**Rellenar automáticamente los elementos del cuadro de herramientas**|Especifica si los controles de usuario y los controles personalizados de la solución actual se muestran en el cuadro de herramientas automáticamente.|

## <a name="settings-blend-only"></a>Configuración (solo en Blend)

Use estas opciones para determinar la configuración al editar archivos XAML con Blend.

|||
|-|-|
|**Zoom mediante**|Acerque el diseñador XAML desplazando la rueda del mouse o presionando la tecla CTRL o ALT al desplazar la rueda del mouse.|
|**Unidades de tipo**|Especifica si las medidas del diseñador se basan en puntos o en píxeles. Como las aplicaciones universales de Windows no admiten los puntos, las unidades se convierten automáticamente en píxeles si **Puntos** está seleccionado.|

## <a name="artboard-blend-only"></a>Mesa de trabajo (solo en Blend)

Use esta configuración para determinar el comportamiento del diseñador XAML al editar documentos XAML en Blend.

### <a name="snapping"></a>Ajuste

|||
|-|-|
|**Mostrar cuadrícula de ajuste**|Cuando esta opción está seleccionada, las líneas de cuadrícula aparecen en el diseñador para ayudarle a alinear controles. Si la opción **Ajustar a líneas de cuadrícula** está seleccionada, los controles agregados al diseñador se ajustan a estas líneas de cuadrícula.|
|**Ajustar a líneas de cuadrícula**|Cuando los controles se agregan o se mueven por el diseñador, se ajustan a las líneas de cuadrícula.|
|**Espaciado entre líneas de cuadrícula**|Especifica el espaciado entre las líneas de cuadrícula en píxeles o puntos (según la configuración de **Unidades de tipo**).|
|**Ajustar a las guías de alineación**|Especifica si los controles se ajustan a las guías de alineación.|
|**Margen predeterminado**|Cuando **Ajustar a las guías de alineación** está habilitado, especifica el espaciado entre el control y las guías de alineación en píxeles o en puntos (según la configuración de **Unidades de tipo**).|
|**Espaciado interno predeterminado**|Cuando **Ajustar a las guías de alineación** está habilitado, especifica el espaciado adicional entre el control y las guías de alineación en píxeles o en puntos (según la configuración de **Unidades de tipo**).|

### <a name="animation"></a>Animación

Use esta configuración para determinar si aparece una advertencia cuando las animaciones dependientes (no aceleradas) están habilitadas en Blend.

### <a name="effects"></a>Efectos

Use esta configuración para determinar si los efectos se representan al editar archivos XAML en el diseñador XAML con Blend.

|||
|-|-|
|**Efectos de representación**|Especifica si los efectos se representan al editar archivos XAML en el diseñador XAML con Blend.|
|**Umbral de zoom**|Especifica el porcentaje de zoom en el que se representan los efectos cuando la casilla **Efectos de representación** está seleccionada. Si aplica zoom más allá de esta configuración, los efectos ya no se representan en el diseñador XAML.|

## <a name="see-also"></a>Vea también

- [XAML en WPF](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [Tutorial: Mi primera aplicación de escritorio WPF](/dotnet/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application)
