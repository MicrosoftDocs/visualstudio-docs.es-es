---
title: Opciones, Editor de texto, Básico (VB), Avanzado
ms.date: 08/12/2020
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Visual_Basic.Editor
- VS.ToolsOptionsPages.Text_Editor.Basic.Editor
- VS.ToolsOptionsPages.Visual_Basic_Editor.Editor
- VS.ToolsOptionsPages.Text_Editor.Basic.SimplifiedEditorPage
- VS.ToolsOptionsPages.Text_Editor.Basic
- VS.ToolsOptionsPages.Text_Editor.Basic.Advanced
- VS.ToolsOptionsPages.Text_Editor.Basic.VB_Specific
helpviewer_keywords:
- Basic Text Editor Options dialog box
ms.assetid: 5a8cafca-f7b4-4a2d-92ce-6894a7673d00
author: akhera99
ms.author: midumont
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 778cd1f9c126b176cafad8b33a147d284bea1b67
ms.sourcegitcommit: 2946d802aec1418e87bfa779d81834eeb7be5c9d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/14/2020
ms.locfileid: "88214655"
---
# <a name="options-text-editor-basic-visual-basic-advanced"></a>Opciones, Editor de texto, Básico (Visual Basic), Avanzado
La página de propiedades **Opciones específicas de VB**, en la carpeta **Básico** de la carpeta **Editor de texto** del cuadro de diálogo **Opciones** (menú **Herramientas**) incluye las propiedades siguientes:

## <a name="analysis"></a>Análisis

- Ámbito del análisis de código activo o del análisis en segundo plano

   Configure el ámbito del análisis en segundo plano para el código administrado. Para obtener más información, vea [Cómo: Configurar el ámbito del análisis activo para el código administrado](../../code-quality/configure-live-code-analysis-scope-managed-code.md).

## <a name="using-directives"></a>Directivas using

- Aplicar primero directivas "System" al ordenar instrucciones Using

   Cuando se selecciona el comando **Eliminar y ordenar instrucciones Using** en el menú contextual, ordena las directivas `using` y coloca los espacios de nombres "System" en la parte superior de la lista.

- Separar grupos de directivas using

   Cuando se selecciona, el comando **Eliminar y ordenar instrucciones Using** en el menú contextual separa las directivas `using` al insertar una línea vacía entre los grupos de directivas con el mismo espacio de nombres raíz.

- Sugerir usos para tipos de ensamblados de referencia
- Sugerir usos para tipos de paquetes NuGet

   Cuando se seleccionan estas opciones, una [acción rápida](../quick-actions.md) se encuentra disponible para instalar un paquete NuGet y agregar una directiva `using` para tipos sin referencia.

   ![Acción rápida para instalar el paquete NuGet en Visual Studio](media/nuget-lightbulb.png)

## <a name="highlighting"></a>Resaltado

 **Habilitar resaltado de referencias y palabras clave**

El editor de texto puede resaltar todas las instancias de un símbolo o todas las palabras clave en una cláusula como `If..Then`, `While...End While` o `Try...Catch...Finally`. Puede navegar entre referencias o palabras clave resaltadas. Para ello, presione **Ctrl** + **Mayús** + **Flecha abajo** o **Ctrl** + **Mayús** + **Flecha arriba**.

## <a name="outlining"></a>esquematizar

**Habilitar modo de esquematización**

Al abrir un archivo en el editor de código, puede ver el documento en el modo de esquematización. Para obtener más información, vea [Esquematización](../../ide/outlining.md). Cuando esta opción está seleccionada, la característica de esquematización se activa al abrir un archivo.

**Mostrar separadores de línea de procedimiento**

El editor de texto indica el ámbito visual de los procedimientos. Se dibuja una línea en los archivos de código fuente *.vb* del proyecto en las ubicaciones indicadas en la tabla siguiente:

|Ubicación en el archivo de código fuente .vb|Ejemplo de ubicación de línea|
|---------------------------------|------------------------------|
|Después del cierre de una construcción de declaración de bloque|- Al final de una clase, estructura, módulo, interfaz o enumeración<br />- Después de una propiedad, función o sub<br />- No entre las cláusulas get y set de una propiedad|
|Después de un conjunto de construcciones de línea única|- Después de las instrucciones Import, antes de una definición de tipo en un archivo de clase<br />- Después de las variables declaradas en una clase, antes de cualquier procedimiento|
|Después de declaraciones de línea única (declaraciones de nivel que no sea de bloque)|- Después de instrucciones Import, instrucciones Inherits, declaraciones de variables, declaraciones de eventos, declaraciones de delegados e instrucciones Declare DLL|

## <a name="block-structure-guides"></a>Guías de estructura de bloque

Cuando se selecciona esta opción, aparecen líneas verticales en el editor que se alinean con bloques de código estructurado, lo que permite identificar fácilmente los bloques de código individuales. Por ejemplo, verá una línea entre `Sub` y `EndSub` en una instrucción `Sub`.

## <a name="editor-help"></a>Ayuda del editor

::: moniker range=">=vs-2019"
**Sugerencias de nombre de parámetro insertado**    
Al seleccionarlo, se insertan sugerencias de nombre de parámetro para literales, literales convertidos e instancias de objeto antes de cada argumento en las llamadas de función.  

![Sugerencias de nombre de parámetro insertado para Visual Basic](media/inline-parameter-name-hints-visualbasic.png)
::: moniker-end

**Lista descriptiva (nuevo formato) de código** El editor de texto vuelve a dar formato al código según corresponda. Cuando se selecciona esta opción, el editor de código hará lo siguiente:

- Alinear el código hasta la posición de tabulación correcta

- Aplicar un uso correcto de las mayúsculas y las minúsculas en las palabras clave, las variables y los objetos

- Agregar el elemento `Then` que falta en una instrucción `If...Then`

- Agregar paréntesis a las llamadas de función

- Agregar las comillas de cierre que faltan en cadenas

- Cambiar el formato de una notación exponencial

- Cambiar el formato de fechas

**Inserción automática de construcciones End**

Cuando escriba, por ejemplo, la primera línea de una declaración de procedimiento, `Sub Main` y presione **ENTRAR**, el editor de texto agregará una línea `End Sub` coincidente. De forma similar, si agrega un bucle [For](/dotnet/visual-basic/language-reference/statements/for-next-statement), el editor de texto agrega una instrucción `Next` coincidente. Cuando se selecciona esta opción, el editor de código agrega automáticamente la construcción End.

**Inserción automática de miembros Interface y MustOverride**

Cuando se confirma una instrucción `Implements` o `Inherits` para una clase, el editor de texto inserta prototipos para los miembros que se deben implementar o invalidar, respectivamente.

**Habilitar sugerencias de corrección de errores**

El editor de texto puede sugerir soluciones para errores comunes y permitirle seleccionar la corrección adecuada, que se aplica después al código.

## <a name="see-also"></a>Vea también

- [General, Entorno, Opciones (Cuadro de diálogo)](../../ide/reference/general-environment-options-dialog-box.md)
- [Opciones, editor de texto, todos los lenguajes, pestañas](../../ide/reference/options-text-editor-all-languages-tabs.md)
