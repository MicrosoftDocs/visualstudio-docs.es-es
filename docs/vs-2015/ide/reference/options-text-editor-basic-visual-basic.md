---
title: Opciones, editor de texto, básico (Visual Basic) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Visual_Basic.Editor
- VS.ToolsOptionsPages.Text_Editor.Basic.Editor
- VS.ToolsOptionsPages.Visual_Basic_Editor.Editor
- VS.ToolsOptionsPages.Text_Editor.Basic.SimplifiedEditorPage
- VS.ToolsOptionsPages.Text_Editor.Basic
- VS.ToolsOptionsPages.Text_Editor.Basic.VB_Specific
helpviewer_keywords:
- Basic Text Editor Options dialog box
ms.assetid: 5a8cafca-f7b4-4a2d-92ce-6894a7673d00
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1edb7ceae1ba187b01b92d64ca33d41d83364e72
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662374"
---
# <a name="options-text-editor-basic-visual-basic"></a>Opciones, editor de texto, básico (Visual Basic)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La página de propiedades **Opciones específicas de VB**, en la carpeta **Básico** de la carpeta **Editor de texto** del cuadro de diálogo **Opciones** (menú **Herramientas**) contiene las propiedades siguientes:

 **Inserción automática de construcciones End** Cuando escribe, por ejemplo, la primera línea de una declaración de procedimiento, `Sub Main—`, y presiona ENTRAR, el editor de texto agrega una línea `End Sub` coincidente. De forma similar, si agrega un bucle [For](https://msdn.microsoft.com/library/f5fc0d51-67ce-4c36-9f09-31c9a91c94e9), el editor de texto agrega una instrucción `Next` coincidente. Cuando se selecciona esta opción, el editor de código agrega automáticamente la construcción End.

 **Lista descriptiva (nuevo formato) de código** El editor de texto vuelve a dar formato al código según corresponda. Cuando se selecciona esta opción, el editor de código hará lo siguiente:

- Alinear el código hasta la posición de tabulación correcta

- Aplicar un uso correcto de las mayúsculas y las minúsculas en las palabras clave, las variables y los objetos

- Agregar el elemento `Then` que falta en una instrucción `If...Then`

- Agregar paréntesis a las llamadas de función

- Agregar las comillas de cierre que faltan en cadenas

- Cambiar el formato de una notación exponencial

- Cambiar el formato de fechas

  **Habilitar el modo de esquematización** Al abrir un archivo en el editor de código, puede ver el documento en el modo de esquematización. Para obtener más información, vea [Esquematización](../../ide/outlining.md). Cuando esta opción está seleccionada, la característica de esquematización se activa al abrir un archivo.

  **Inserción automática de miembros Interface y MustOverride** Cuando se confirma una instrucción `Implements` o una instrucción `Inherits` para una clase, el editor de texto inserta prototipos para los miembros que se deben implementar o reemplazar, respectivamente.

  **Mostrar separadores de líneas de procedimientos** El editor de texto indica el ámbito visual de los procedimientos. Se dibuja una línea en los archivos de código fuente .vb del proyecto en las ubicaciones indicadas en la tabla siguiente:

|Ubicación en el archivo de código fuente .vb|Ejemplo de ubicación de línea|
|---------------------------------|------------------------------|
|Después del cierre de una construcción de declaración de bloque|- Al final de una clase, estructura, módulo, interfaz o enumeración<br />- Después de una propiedad, función o sub<br />- No entre las cláusulas get y set de una propiedad|
|Después de un conjunto de construcciones de línea única|- Después de las instrucciones Import, antes de una definición de tipo en un archivo de clase<br />- Después de las variables declaradas en una clase, antes de cualquier procedimiento|
|Después de declaraciones de línea única (declaraciones de nivel que no sea de bloque)|- Después de instrucciones Import, instrucciones Inherits, declaraciones de variables, declaraciones de eventos, declaraciones de delegados e instrucciones Declare DLL|

 **Habilitar sugerencias de corrección de errores** El editor de texto puede sugerir soluciones a errores comunes y permite seleccionar la corrección adecuada que se aplica a su código.

 **Habilitar el resaltado de referencias y palabras clave** El editor de texto puede resaltar todas las instancias de un símbolo o todas las palabras clave de una cláusula como `If..Then`, `While...End While` o `Try...Catch...Finally`. Puede navegar entre referencias o palabras clave resaltadas. Para ello, presione CTRL+Mayús+flecha abajo o CTRL+Mayús+flecha arriba.

## <a name="see-also"></a>Otras referencias
 Opciones del [cuadro de diálogo general, entorno, opciones](../../ide/reference/general-environment-options-dialog-box.md) [, editor de texto, todos los lenguajes, tabulaciones](../../ide/reference/options-text-editor-all-languages-tabs.md)
