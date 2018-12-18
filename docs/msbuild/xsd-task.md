---
title: XSD (tarea) | Microsoft Docs
ms.custom: ''
ms.date: 06/27/2018
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- vc.task.xsd
- VC.Project.VCXMLDataGeneratorTool.Namespace
- VC.Project.VCXMLDataGeneratorTool.GenerateFromSchema
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- XSD task (MSBuild (Visual C++))
- MSBuild (Visual C++), XSD task
ms.assetid: 15c99f5c-7124-4bbc-bc03-70c7bcce8893
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3eb81e05a16eb504b14e94de2c1270057311b85a
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2018
ms.locfileid: "39231602"
---
# <a name="xsd-task"></a>XSD (tarea)
Encapsula la herramienta de definición de esquema XML (*xsd.exe*), que genera archivos de esquema o clase desde un origen.  

> [!NOTE]
> En Visual Studio 2017, el proyecto C++ ya no es compatible con *xsd.exe*. Puede seguir usando la API **Microsoft.VisualC.CppCodeProvider** agregando manualmente *CppCodeProvider.dll* a la GAC. 
  
## <a name="parameters"></a>Parámetros  
 En la siguiente tabla se describen los parámetros de la tarea **XSD**.  
  
-   **AdditionalOptions**  
  
     Parámetro **String** opcional.  
  
     Una lista de opciones especificada en la línea de comando. Por ejemplo, /\<option1> /\<option2> /\<option#>. Utilice este parámetro para especificar opciones que no están representadas por ningún otro parámetro de tarea **XSD**.  
  
-   **GenerateFromSchema**  
  
     Parámetro **String** opcional.  
  
     Especifica los tipos que se generan a partir del esquema especificado.  
  
     Especifique uno de los valores siguientes, cada uno de los cuales corresponde a una opción XSD.  
  
    -   **classes** - **/classes**  
  
    -   **dataset** - **/dataset**  
  
-   **Idioma**  
  
     Parámetro **String** opcional.  
  
     Especifica el lenguaje de programación a utilizar para el código generado.  
  
     Elija entre **CS** (C#, que es el valor predeterminado), **VB** (Visual Basic) o **JS** (JScript). También se puede especificar un nombre completo para una clase que implemente `System.CodeDom.Compiler.CodeDomProvider Class`.  
  
-   **Namespace**  
  
     Parámetro **String** opcional.  
  
     Especifica el espacio de nombres del motor en tiempo de ejecución para los tipos generados.  
  
-   **Sources**  
  
     Parámetro `ITaskItem[]` requerido.  
  
     Define una matriz de elementos de archivo origen de MSBuild que las tareas pueden consumir y emitir.  
  
-   **SuppressStartupBanner**  
  
     Parámetro **Boolean** opcional.  
  
     Si es `true`, evita que se muestre el copyright y el mensaje de número de versión cuando la tarea se inicia.   
  
-   **TrackerLogDirectory**  
  
     Parámetro **String** opcional.  
  
     Especifica el directorio de registro de seguimiento.  
  
## <a name="see-also"></a>Vea también  
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)