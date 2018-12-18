---
title: Opciones, editor de texto, C#, avanzado
ms.date: 10/29/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Outlining
- VS.ToolsOptionsPages.Text_Editor.CSharp.Advanced
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 7cfbc6d57e5bfd3c6a8f317967448039a9b3f5e4
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50670720"
---
# <a name="options-text-editor-c-advanced"></a>Opciones, editor de texto, C#, avanzado

Use la página de opciones **Avanzado** para modificar la configuración del formato del editor, la refactorización de código y los comentarios de documentación XML para C#. Para obtener acceso a esta página de opciones, elija **Herramientas** > **Opciones** y, después, elija **Editor de texto** > **C#** > **Avanzado**.

> [!NOTE]
> Puede ser que aquí no aparezcan todas las opciones.

## <a name="analysis"></a>Análisis

- Habilitar análisis de la solución completa

   Habilita el análisis de código en todos los archivos de la solución, no solo en los archivos de código abiertos. Para más información, vea [Full solution analysis](../../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md) (Análisis de la solución completa).

## <a name="using-directives"></a>Directivas using

- Aplicar primero directivas "System" al ordenar instrucciones Using

   Cuando se selecciona el comando **Eliminar y ordenar instrucciones Using** en el menú contextual, ordena las directivas `using` y coloca los espacios de nombres "System" en la parte superior de la lista.

   Antes de ordenar:

   ```csharp
   using AutoMapper;
   using FluentValidation;
   using System.Collections.Generic;
   using System.Linq;
   using Newtonsoft.Json;
   using System;
   ```
   
   Después de ordenar:

   ```csharp
   using System;
   using System.Collections.Generic;
   using System.Linq;
   using AutoMapper;
   using FluentValidation;
   using Newtonsoft.Json;
   ```
   
- Separar grupos de directivas using

   Cuando se selecciona, el comando **Eliminar y ordenar instrucciones Using** en el menú contextual separa las directivas `using` al insertar una línea vacía entre los grupos de directivas con el mismo espacio de nombres raíz.

   Antes de ordenar:

   ```csharp
   using AutoMapper;
   using FluentValidation;
   using System.Collections.Generic;
   using System.Linq;
   using Newtonsoft.Json;
   using System;
   ```
   
   Después de ordenar:
   
   ```csharp
   using AutoMapper;
   
   using FluentValidation;
   
   using Newtonsoft.Json;
   
   using System;
   using System.Collections.Generic;
   using System.Linq;
   ```
   
- Sugerir usos para tipos de ensamblados de referencia 
- Sugerir usos para tipos de paquetes NuGet 

   Cuando se seleccionan estas opciones, una [acción rápida](../quick-actions.md) se encuentra disponible para instalar un paquete NuGet y agregar una directiva `using` para tipos sin referencia.

   ![Acción rápida para instalar el paquete NuGet en Visual Studio](media/nuget-lightbulb.png)
  
## <a name="highlighting"></a>Resaltado

- Resaltar referencias al símbolo bajo el cursor

   Cuando el cursor esté colocado dentro de un símbolo, o cuando haga clic en un símbolo, todas las instancias de ese símbolo en el archivo de código se resaltan.

## <a name="outlining"></a>esquematizar

- Especificar el modo de esquematización al abrir los archivos

   Cuando está seleccionada, esquematiza automáticamente el archivo de código, lo que crea bloques contraíbles de código. La primera vez que se abre un archivo, los bloques #regions y los bloques de código inactivos se contraen.

- Mostrar separadores de línea de procedimientos

   El editor de texto indica el ámbito visual de los procedimientos. Se dibuja una línea en los archivos de código fuente *.vb* del proyecto en las ubicaciones indicadas en la tabla siguiente:

   |Ubicación en el archivo de código fuente .vb|Ejemplo de ubicación de línea|
   |---------------------------------|------------------------------|
   |Después del cierre de una construcción de declaración de bloque|- Al final de una clase, estructura, módulo, interfaz o enumeración<br />- Después de una propiedad, función o sub<br />- No entre las cláusulas get y set de una propiedad|
   |Después de un conjunto de construcciones de línea única|- Después de las instrucciones Import, antes de una definición de tipo en un archivo de clase<br />- Después de las variables declaradas en una clase, antes de cualquier procedimiento|
   |Después de declaraciones de línea única (declaraciones de nivel que no sea de bloque)|- Después de instrucciones Import, instrucciones Inherits, declaraciones de variables, declaraciones de eventos, declaraciones de delegados e instrucciones Declare DLL|

## <a name="editor-help"></a>Ayuda del editor

- Generar comentarios de documentación XML para ///

   Cuando se selecciona, inserta los elementos XML de los comentarios de documentación XML después de escribir la introducción de comentario `///`. Para más información sobre la documentación XML, vea [Comentarios de documentación XML (Guía de programación de C#)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments).

## <a name="see-also"></a>Vea también

- [Cómo insertar comentarios XML para la generación de documentación](../../ide/reference/generate-xml-documentation-comments.md)
- [Comentarios de documentación XML (Guía de programación de C#)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)
- [Documentar el código con comentarios XML (Guía de C#)](/dotnet/csharp/codedoc)
- [Opciones del editor específicas del lenguaje](../../ide/reference/setting-language-specific-editor-options.md)
- [IntelliSense para C#](../../ide/visual-csharp-intellisense.md)
