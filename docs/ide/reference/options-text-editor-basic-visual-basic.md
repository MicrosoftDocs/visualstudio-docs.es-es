---
title: Opciones, editor de texto, básico (Visual Basic)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 27048b5d70674cd492227e96682f8401ed7160ee
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="options-text-editor-basic-visual-basic"></a>Opciones, editor de texto, básico (Visual Basic)
La página de propiedades **Opciones específicas de VB**, en la carpeta **Básico** de la carpeta **Editor de texto** del cuadro de diálogo **Opciones** (menú **Herramientas**) contiene las propiedades siguientes:

 **Inserción automática de construcciones End** Cuando escribe, por ejemplo, la primera línea de una declaración de procedimiento, `Sub Main—`, y presiona ENTRAR, el editor de texto agrega una línea `End Sub` coincidente. De forma similar, si agrega un bucle [For](/dotnet/visual-basic/language-reference/statements/for-next-statement), el editor de texto agrega una instrucción `Next` coincidente. Cuando se selecciona esta opción, el editor de código agrega automáticamente la construcción End.

 **Lista descriptiva (nuevo formato) de código** El editor de texto vuelve a dar formato al código según corresponda. Cuando se selecciona esta opción, el editor de código hará lo siguiente:

-   Alinear el código hasta la posición de tabulación correcta

-   Aplicar un uso correcto de las mayúsculas y las minúsculas en las palabras clave, las variables y los objetos

-   Agregar el elemento `Then` que falta en una instrucción `If...Then`

-   Agregar paréntesis a las llamadas de función

-   Agregar las comillas de cierre que faltan en cadenas

-   Cambiar el formato de una notación exponencial

-   Cambiar el formato de fechas

**Habilitar modo de esquematización**

Al abrir un archivo en el editor de código, puede ver el documento en el modo de esquematización. Para obtener más información, vea [Esquematización](../../ide/outlining.md). Cuando esta opción está seleccionada, la característica de esquematización se activa al abrir un archivo.

**Inserción automática de miembros Interface y MustOverride**

Cuando se confirma una instrucción `Implements` o `Inherits` para una clase, el editor de texto inserta prototipos para los miembros que se deben implementar o invalidar, respectivamente.

**Mostrar separadores de línea de procedimiento**

El editor de texto indica el ámbito visual de los procedimientos. Se dibuja una línea en los archivos de código fuente .vb del proyecto en las ubicaciones indicadas en la tabla siguiente:

|Ubicación en el archivo de código fuente .vb|Ejemplo de ubicación de línea|
|---------------------------------|------------------------------|
|Después del cierre de una construcción de declaración de bloque|- Al final de una clase, estructura, módulo, interfaz o enumeración<br />- Después de una propiedad, función o sub<br />- No entre las cláusulas get y set de una propiedad|
|Después de un conjunto de construcciones de línea única|- Después de las instrucciones Import, antes de una definición de tipo en un archivo de clase<br />- Después de las variables declaradas en una clase, antes de cualquier procedimiento|
|Después de declaraciones de línea única (declaraciones de nivel que no sea de bloque)|- Después de instrucciones Import, instrucciones Inherits, declaraciones de variables, declaraciones de eventos, declaraciones de delegados e instrucciones Declare DLL|

**Habilitar sugerencias de corrección de errores**

El editor de texto puede sugerir soluciones para errores comunes y permitirle seleccionar la corrección adecuada, que se aplica después al código.

**Habilitar resaltado de referencias y palabras clave**

El editor de texto puede resaltar todas las instancias de un símbolo o todas las palabras clave en una cláusula como `If..Then`, `While...End While` o `Try...Catch...Finally`. Puede navegar entre referencias o palabras clave resaltadas. Para ello, presione CTRL+Mayús+flecha abajo o CTRL+Mayús+flecha arriba.

## <a name="see-also"></a>Vea también

- [General, Entorno, Opciones (Cuadro de diálogo)](../../ide/reference/general-environment-options-dialog-box.md)
- [Opciones, editor de texto, todos los lenguajes, pestañas](../../ide/reference/options-text-editor-all-languages-tabs.md)