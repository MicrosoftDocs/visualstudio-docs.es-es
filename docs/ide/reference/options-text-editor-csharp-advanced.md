---
title: Opciones, editor de texto, C#, avanzado
description: Obtenga información sobre cómo usar la página Avanzadas de la sección C# para modificar la configuración de formato del editor, la refactorización de código y los comentarios de documentación XML para C#.
ms.custom: SEO-VS-2020
ms.date: 06/01/2021
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Outlining
- VS.ToolsOptionsPages.Text_Editor.CSharp.Advanced
author: mikadumont
ms.author: midumont
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 29f6dd2b4a101132bc7bc19664c51fd5d4b8283e
ms.sourcegitcommit: f50bbdb15c4f9fca0fa245ca765183c378960cc5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/03/2021
ms.locfileid: "111351998"
---
# <a name="options-text-editor-c-advanced"></a>Opciones, editor de texto, C#, avanzado

Use la página de opciones **Avanzado** para modificar la configuración del formato del editor, la refactorización de código y los comentarios de documentación XML para C#. Para obtener acceso a esta página de opciones, elija **Herramientas** > **Opciones** y, después, elija **Editor de texto** > **C#**  > **Avanzado**.

> [!NOTE]
> Puede ser que aquí no aparezcan todas las opciones.

## <a name="analysis"></a>Análisis

- Ámbito del análisis de código activo o del análisis en segundo plano

   Configure el ámbito del análisis en segundo plano para el código administrado. Para obtener más información, vea [Cómo: Configurar el ámbito del análisis activo para el código administrado](../../code-quality/configure-live-code-analysis-scope-managed-code.md).

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

::: moniker range=">=vs-2019"                                              
- Sugerir usos para tipos en ensamblados .NET Framework
::: moniker-end
                                         
::: moniker range="vs-2017"                                                
- Sugerir usos para tipos de ensamblados de referencia
::: moniker-end                                                            

- Sugerir usos para tipos de paquetes NuGet

   Cuando se seleccionan estas opciones, una [acción rápida](../quick-actions.md) se encuentra disponible para instalar un paquete NuGet y agregar una directiva `using` para tipos sin referencia.

   ![Acción rápida para instalar el paquete NuGet en Visual Studio](media/nuget-lightbulb.png)

- Agregar las directivas using que faltan al pegar

    Cuando se selecciona esta opción, las directivas `using` se agregarán automáticamente al código al pegar un tipo en un archivo.

## <a name="highlighting"></a>Resaltado

- Resaltar referencias al símbolo bajo el cursor

   Cuando el cursor esté colocado dentro de un símbolo, o cuando haga clic en un símbolo, todas las instancias de ese símbolo en el archivo de código se resaltan.

## <a name="outlining"></a>esquematizar

- Especificar el modo de esquematización al abrir los archivos

   Cuando está seleccionada, esquematiza automáticamente el archivo de código, lo que crea bloques contraíbles de código. La primera vez que se abre un archivo, los bloques #regions y los bloques de código inactivos se contraen.

- Mostrar separadores de línea de procedimientos

   El editor de texto indica el ámbito visual de los procedimientos. Se dibuja una línea en los archivos de código fuente *.cs* del proyecto en las ubicaciones indicadas en la tabla siguiente:

   |Ubicación en el archivo de código fuente .cs|Ejemplo de ubicación de línea|
   |---------------------------------|------------------------------|
   |Después del cierre de una construcción de declaración de bloque|- Al final de una clase, estructura, módulo, interfaz o enumeración<br />- Después de una propiedad, función o sub<br />- No entre las cláusulas get y set de una propiedad|
   |Después de un conjunto de construcciones de línea única|- Después de las instrucciones Import, antes de una definición de tipo en un archivo de clase<br />- Después de las variables declaradas en una clase, antes de cualquier procedimiento|
   |Después de declaraciones de línea única (declaraciones de nivel que no sea de bloque)|- Después de instrucciones Import, instrucciones Inherits, declaraciones de variables, declaraciones de eventos, declaraciones de delegados e instrucciones Declare DLL|

## <a name="block-structure-guides"></a>Guías de estructura de bloque

Active estas casillas de verificación para mostrar líneas punteadas verticales las llaves ( **{}** ) en el código. De este modo, puede ver con facilidad los bloques individuales de código para las construcciones de nivel de declaración y de nivel de código.

## <a name="comments"></a>Comentarios

- Generar comentarios de documentación XML para ///

   Cuando se selecciona, inserta los elementos XML de los comentarios de documentación XML después de escribir la introducción de comentario `///`. Para más información sobre la documentación XML, vea [Comentarios de documentación XML (Guía de programación de C#)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments).

::: moniker range=">=vs-2019"

## <a name="inline-hints"></a>Sugerencias insertadas

- Sugerencias de nombre de parámetro insertado 
    
    Al seleccionarlo, se insertan sugerencias de nombre de parámetro para literales, literales convertidos e instancias de objeto antes de cada argumento en las llamadas de función.  
    
    ![Sugerencias de nombre de parámetro insertado para CSharp](media/inline-parameter-name-hints-csharp.png)

- Sugerencias de tipos alineados 
    
    Cuando se seleccionan, se insertan sugerencias de tipos para variables con tipos inferidos y tipos de parámetro lambda.  
    
    ![Sugerencias de tipos alineados para CSharp](media/inline-type-hints-csharp.png)

## <a name="inheritance-margin"></a>Margen de herencia 

- Al seleccionarlo, se agregan iconos a los márgenes que representan las implementaciones e invalidaciones del código. Al hacer clic en el icono del margen de herencia se mostrarán las opciones de herencia que puede seleccionar para navegar a ellas.

    ![Margen de herencia](media/inheritance-margin.png)

::: moniker-end

## <a name="see-also"></a>Vea también

- [Cómo: Insertar comentarios XML para la generación de documentación](../../ide/reference/generate-xml-documentation-comments.md)
- [Comentarios de documentación XML (Guía de programación de C#)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)
- [Documentar el código con comentarios XML (Guía de C#)](/dotnet/csharp/codedoc)
- [Opciones del editor específicas del lenguaje](../../ide/reference/setting-language-specific-editor-options.md)
- [IntelliSense para C#](../../ide/visual-csharp-intellisense.md)
