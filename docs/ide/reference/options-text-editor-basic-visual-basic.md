---
title: "Opciones, editor de texto, b&#225;sico (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ToolsOptionsPages.Visual_Basic.Editor"
  - "VS.ToolsOptionsPages.Text_Editor.Basic.Editor"
  - "VS.ToolsOptionsPages.Visual_Basic_Editor.Editor"
  - "VS.ToolsOptionsPages.Text_Editor.Basic.SimplifiedEditorPage"
  - "VS.ToolsOptionsPages.Text_Editor.Basic"
  - "VS.ToolsOptionsPages.Text_Editor.Basic.VB_Specific"
helpviewer_keywords: 
  - "Basic-Editor de texto-Opciones (cuadro de diálogo)"
ms.assetid: 5a8cafca-f7b4-4a2d-92ce-6894a7673d00
caps.latest.revision: 15
caps.handback.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Opciones, editor de texto, b&#225;sico (Visual Basic)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

La página de propiedades **Opciones específicas de VB**, en la carpeta **Basic** de la carpeta **Editor de texto** del cuadro de diálogo **Opciones** \(menú **Herramientas**\), contiene las siguientes propiedades:  
  
 **Inserción automática de construcciones End**  
 Cuando escribe, por ejemplo, la primera línea de una declaración de procedimiento, `Sub Main—`, y presiona ENTRAR, el editor de texto agrega una línea `End Sub` correspondiente.  De forma similar, si agrega un bucle [For](/dotnet/visual-basic/language-reference/statements/for-next-statement), el editor de texto agrega una instrucción `Next` correspondiente.  Cuando esta opción está seleccionada, el editor de código agrega automáticamente la construcción End.  
  
 **Lista descriptiva \(nuevo formato\) de código**  
 El editor de texto vuelve a dar el formato apropiado al código.  Cuando se selecciona esta opción, el editor de código hará lo siguiente:  
  
-   Alinear el código hasta la posición de tabulación correcta.  
  
-   Volver a poner el formato correcto de mayúsculas o minúsculas a las palabras clave, las variables y los objetos.  
  
-   Agregar `Then` a una instrucción `If...Then` si éste último faltara.  
  
-   Agregar paréntesis a las llamadas a funciones.  
  
-   Agregar a las cadenas comillas de cierre que falten.  
  
-   Volver a dar formato a la notación exponencial.  
  
-   Volver a dar formato a las fechas.  
  
 **Habilitar modo de esquematización**  
 Cuando abre un archivo en el editor de código, puede ver el documento en modo de esquematización.  Para obtener más información, consulte [Esquematización](../../ide/outlining.md).  Cuando esta opción está seleccionada, la característica de esquematización se habilita al abrir un archivo.  
  
 **Inserción automática de miembros Interface y MustOverride**  
 Al confirmar una instrucción `Implements` o `Inherits` para una clase, el editor de texto inserta prototipos para los miembros que se deben implementar o invalidar, respectivamente.  
  
 **Mostrar separadores de línea de procedimientos**  
 El editor de texto indica el ámbito visual de los procedimientos.  Se dibuja una línea en los archivos de código fuente .vb del proyecto, en las ubicaciones citadas en la siguiente tabla:  
  
|Ubicación en el archivo de código fuente .vb|Ejemplo de la ubicación de la línea|  
|--------------------------------------------------|-----------------------------------------|  
|Tras el cierre de una construcción de declaración de bloque|-   Al final de una clase, estructura, módulo, interfaz o enumeración<br />-   Tras una propiedad, función o subproceso<br />-   No entre las cláusulas get y set de una propiedad|  
|Tras un conjunto de construcciones de una sola línea|-   Después de las instrucciones import y antes de una definición de tipo en un archivo de clase<br />-   Después de las variables declaradas en una clase y antes de cualquier procedimiento|  
|Después de declaraciones de una sola línea \(declaraciones de no bloque\)|-   Después de instrucciones import e inherits; declaraciones de variables, eventos y delegados; e instrucciones de declaración de DLL|  
  
 **Habilitar sugerencias de corrección de errores**  
 El editor de texto puede sugerir soluciones a los errores frecuentes y permitirle seleccionar la corrección adecuada, que se aplicará entonces al código.  
  
 **Habilitar resaltado de referencias y palabras clave**  
 El editor de texto puede resaltar todas las instancias de un símbolo o todas las palabras clave de una cláusula como `If..Then`, `While...End While` o `Try...Catch...Finally`.  Puede navegar entre referencias resaltadas o palabras clave presionando CTRL\+MAYÚS\+FLECHA ABAJO o CTRL\+MAYÚS\+FLECHA ARRIBA.  
  
## Vea también  
 [General, Entorno, Opciones \(Cuadro de diálogo\)](../../ide/reference/general-environment-options-dialog-box.md)   
 [Opciones, editor de texto, todos los lenguajes, pestañas](../../ide/reference/options-text-editor-all-languages-tabs.md)