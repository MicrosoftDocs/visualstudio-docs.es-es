---
title: Opciones, Diseñador de Windows Forms, General
description: Obtenga información sobre cómo usar la página General para establecer preferencias para las cuadrículas y otras características de Diseñador de Windows Forms en Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 08/09/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.WindowsFormsDesigner.General
helpviewer_keywords:
- Windows Forms Designer options
- Options dialog box, Windows Forms Designer
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.openlocfilehash: c55d3dae96ff2757c8a9ba1969c378aa2290d716
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99932259"
---
# <a name="options-dialog-box-windows-forms-designer"></a>Cuadro de diálogo Opciones: Diseñador de Windows Forms

La página de opciones del Diseñador de Windows Forms le permite establecer las preferencias para las cuadrículas y otras características del Diseñador de Windows Forms de Visual Studio. Abra el cuadro de diálogo **Opciones** desde el menú **Herramientas**.

## <a name="code-generation-settings"></a>Configuración de la generación de código

**Generación de código optimizado**\
Permite la generación de código optimizado. Es posible que algunos controles no sean compatibles con este modo. Para que este cambio surta efecto, se debe cerrar Visual Studio y volver a abrirlo.

## <a name="high-dpi-support"></a>Compatibilidad con valores altos de PPP

**Notificaciones de escalado de PPP**\
Muestre un mensaje en el Diseñador de Windows Forms de que es posible reiniciar Visual Studio con un escalado del 100 %. Para más información, consulte [Deshabilitación del reconocimiento de PPP en Visual Studio](/dotnet/framework/winforms/disable-dpi-awareness-visual-studio).

## <a name="layout-settings"></a>Configuración de diseño

**Tamaño de celda de cuadrícula predeterminado**\
Establece el espaciado, en píxeles, entre las líneas de cuadrícula horizontales y verticales del diseñador. El tamaño predeterminado es 8, 8. El tamaño máximo es 200, 200.

**Modo de diseño**\
Especifica el sistema de alineación que se va a usar para el diseño. Puede elegir entre SnapToGrid o Snaplines.

**Mostrar cuadrícula**\
Especifica si los diseñadores muestran la cuadrícula de ajuste de tamaño. De manera predeterminada, la cuadrícula está activada.

**Ajustar a la cuadrícula**\
Determina si los diseñadores ajustarán los objetos y controles a la cuadrícula. En otras palabras, el ajuste de tamaño y el movimiento de los elementos del diseñador se restringen según el incremento de GridSize cuando esta característica está activada. Cuando la característica SnapToGrid está activada, es más sencillo alinear los distintos aspectos de la interfaz de usuario de manera precisa, pero se limita la libertad con la que es posible ubicar los controles. De manera predeterminada, SnapToGrid está activado.

## <a name="object-bound-smart-tag-settings"></a>Configuraciones de etiquetas inteligentes enlazadas a objetos

**Abrir automáticamente etiquetas inteligentes**\
Determina si los controles y componentes muestran etiquetas inteligentes. No todos los controles y componentes admiten las etiquetas inteligentes.

## <a name="refactoring"></a>Refactorización

**Habilitar refactorización en cambios de nombre**\
Cuando se establece en `true`, se realiza una operación de refactorización de cambio de nombre cuando se cambia el nombre de un componente en la ventana Propiedades o en la ventana Esquema del documento.

## <a name="toolbox"></a>Cuadro de herramientas

**Rellenar automáticamente la ventana Cuadro de herramientas**\
Determina si la ventana Cuadro de herramientas se rellena de manera automáticamente con componentes y controles compilados por el proyecto.
