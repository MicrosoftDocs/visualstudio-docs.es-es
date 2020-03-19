---
title: Opciones, Editor de texto, HTML (formularios Web Forms), formato
ms.date: 1/15/2019
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.HTML.Format
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9e28caf7f71af7c7a07634d1732a1001a32a4aee
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2020
ms.locfileid: "75568326"
---
# <a name="options-text-editor-html-web-forms-formatting"></a>Opciones, Editor de texto, HTML (formularios Web Forms), formato

Use la página de opciones **Formato** para establecer las opciones de proyecto HTML para dar formato al código en el Editor de código. Para acceder a esta página, en la barra de menús elija **Herramientas** > **Opciones** y expanda **Editor de texto** > **HTML (formularios Web Forms)**  > **Formato**.

## <a name="capitalization"></a>Uso de mayúsculas

Cuando se seleccionan estas opciones, los editores XML y de la vista Código fuente aplican un formato de mayúsculas y minúsculas predeterminado a los nombres de elementos y atributos, cuando se crean por primera vez y durante el formato automático. La configuración **Aplicar formato automático** determina el momento en que se aplica nuevamente el formato de manera automática.

> [!WARNING]
> XML distingue entre mayúsculas y minúsculas. Establecer de forma predeterminada el uso de mayúsculas y minúsculas puede afectar a los analizadores XML.

### <a name="uielement-list"></a>Lista de UIElement

**Etiqueta de servidor, atributos de servidor**

Estas opciones especifican el modo en que se usan las mayúsculas y minúsculas en el código de marcado para los controles de servidor web.

|Opción|Resultado|
|---------------------------------|------------------------------|
|**Tal y como se escriba**|El uso de mayúsculas y minúsculas en el elemento es exactamente como lo escribe.|
|**Mayúsculas**|Los nombres de los elementos se cambian a mayúsculas.|
|**Minúsculas**|Los nombres de los elementos se cambian a minúsculas.|
|**Definición de ensamblado**|El uso de mayúsculas y minúsculas viene determinado por el modo en que se define el elemento en la clase del tipo correspondiente.|

**Etiqueta de cliente, atributos de cliente**

Estas opciones especifican si el formato automático cambia los nombres de los atributos y propiedades HTML a mayúsculas o minúsculas, o si los deja tal como se escribieron.

|Opción|Resultado|
|---------------------------------|------------------------------|
|**Tal y como se escriba**|El uso de mayúsculas y minúsculas en el atributo es exactamente como lo escribe.|
|**Mayúsculas**|Los nombres de los atributos cambian a mayúsculas.|
|**Minúsculas**|Los nombres de los atributos cambian a minúsculas.|

## <a name="automatic-formatting-options"></a>Opciones de formato automático

Estas opciones hacen que el Editor de vistas de código fuente agregue o quite saltos de línea físicos durante el formato automático. También puede especificar si el editor agrega los atributos entre comillas.

> [!NOTE]
> Estas opciones no modifican el uso de espacios en blanco dentro del código de marcado XML.

### <a name="uielement-list"></a>Lista de UIElement

- **Insertar comillas de valores de atributos al escribir**

   Cuando se selecciona esta opción, el editor coloca automáticamente los atributos entre comillas cuando se escriben (por ejemplo: ID="Select1"). Desactive esta opción si prefiere insertar las comillas manualmente.

   > [!NOTE]
   > Tanto si se selecciona esta opción como si no, todas las comillas existentes en el código de marcado se conservan; las comillas nunca se eliminan.

- **Insertar comillas de valores de atributos al aplicar formato**

   Cuando se selecciona esta opción, la función de formato automático coloca los valores de los atributos entre comillas (por ejemplo: ID="Select1").

   > [!NOTE]
   > Tanto si se selecciona esta opción como si no, todas las comillas existentes en el código de marcado se conservan.

- **Insertar automáticamente etiqueta de cierre**

   Cuando se selecciona esta opción, el editor crea automáticamente una etiqueta de cierre (por ejemplo, **\</b>** ) cuando se cierra la etiqueta de apertura.

## <a name="tag-wrapping"></a>Ajuste de etiquetas

Estas opciones determinan si el editor divide las etiquetas entre las líneas si sobrepasan una cierta longitud.

### <a name="uielement-list"></a>Lista de UIElement

- **Ajustar etiquetas cuando superen la longitud especificada**

   Cuando se selecciona esta opción, el editor divide las etiquetas entre las líneas si la etiqueta supera la longitud especificada en el cuadro de texto **Longitud**. Esta acción solo ocurre al dar formato a la etiqueta y no cuando se escribe una nueva.

   > [!NOTE]
   > El valor que se especifique se usará como valor mínimo. El editor no divide atributos individuales.

- **Longitud**

   Especifica el número de caracteres que se van a mostrar en una línea antes del ajuste. Este cuadro de entrada está deshabilitado a menos que esté activada la casilla **Ajustar etiquetas cuando superen la longitud especificada**.

- **Opciones específicas de etiqueta**

   Muestra el cuadro de diálogo **Opciones específicas de etiqueta** que le permite establecer opciones de formato para etiquetas individuales o grupos de etiquetas.

## <a name="see-also"></a>Vea también

- [General, Entorno, Opciones (Cuadro de diálogo)](../../ide/reference/general-environment-options-dialog-box.md)
