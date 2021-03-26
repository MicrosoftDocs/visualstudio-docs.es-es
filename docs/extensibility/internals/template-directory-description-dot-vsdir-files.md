---
title: Descripción del directorio de plantillas (. Archivos vsdir) | Microsoft Docs
description: Obtenga información sobre cómo un archivo de Descripción del directorio de plantillas permite que el IDE de Visual Studio muestre carpetas, archivos. vsz y plantillas asociadas con el proyecto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .vsdir files
- VSDIR files
- template directory description files
ms.assetid: 9df51800-190e-4662-b685-fdaafcff1400
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: bdd21dfa9fe5aae11553bb0268017690aba46fe9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105080507"
---
# <a name="template-directory-description-vsdir-files"></a>Archivos de descripción del directorio de plantilla (.Vsdir)
Un archivo de Descripción del directorio de plantillas (. vsdir) es un archivo de texto que permite al entorno de desarrollo integrado (IDE) Mostrar carpetas, archivos. vsz del asistente y archivos de plantilla asociados al proyecto en los cuadros de diálogo. El contenido incluye un registro por archivo o carpeta. Se combinan todos los archivos. vsdir en una ubicación a la que se hace referencia, aunque en general solo se proporciona un archivo. vsdir para describir varias carpetas, asistentes o archivos de plantilla.

 Las carpetas (subdirectorios), los archivos a los que se hace referencia en el archivo. vsdir y el archivo. vsdir se encuentran en el mismo directorio. Cuando el IDE ejecuta un asistente o muestra una carpeta o un archivo en los cuadros de diálogo **nuevo proyecto** o **Agregar nuevo elemento** , el IDE examina el directorio que contiene los archivos ejecutados para determinar si hay un archivo. vsdir presente. Si se encuentra un archivo. vsdir, el IDE lo lee para determinar si contiene una entrada para la carpeta o el archivo ejecutados o mostrados. Si se encuentra una entrada, el IDE usa la información en la ejecución del asistente o la visualización del contenido.

 El siguiente ejemplo de código es del archivo SourceFiles. vsdir en la \<EnvSDK> clave del registro \bscprj\bscprj\bscprjprojectitems\ Source_Files:

```
HeaderFile.h|{E59935A1-6156-11d1-87A6-00A0C91E2A46}|#125|130|#126|0|0|0|#127
SourceFile.cpp|{E59935A1-6156-11d1-87A6-00A0C91E2A46}|#122|110|#123|0|0|0|#124
```

 En este caso, dos registros se encuentran en un archivo. Una nueva línea (carácter de retorno de carro) separa cada registro. Cada línea representa un tipo de archivo diferente. Un carácter de barra vertical (&#124;) separa los campos de cada registro. Un único directorio puede contener varios archivos. vsdir que tengan nombres de archivo diferentes, o bien puede tener un archivo. vsdir para cada tipo de archivo.

## <a name="fields"></a>Campos
 En la tabla siguiente se enumeran los campos especificados para cada registro.

| Campo | Descripción |
| - | - |
| Nombre de ruta de acceso relativa (RelPathName) | El nombre de la carpeta, plantilla o archivo. vsz, como HeaderFile. h o mi Wizard. vsz. Este campo también puede ser un nombre que se usa para representar una carpeta. |
| {clsidPackage} | GUID del VSPackage que permite el acceso a cadenas localizadas, como LocalizedName, Description, IconResourceId y SuggestedBaseName, en los recursos de la biblioteca de vínculos dinámicos (DLL) satélite del VSPackage. IconResourceId se aplica si no se proporciona DLLPath. **Nota:**  Este campo es opcional a menos que uno o varios de los campos anteriores sean un identificador de recursos. Normalmente, este campo está en blanco para los archivos. vsdir que corresponden a asistentes de terceros que no localizan su texto. |
| LocalizedName | Nombre localizado del archivo de plantilla o asistente. Este campo puede ser una cadena o un identificador de recursos con el formato "#ResID". Este nombre se muestra en el cuadro de diálogo **Agregar nuevo elemento** . **Nota:**  Si LocalizedName es un identificador de recursos, se requiere {clsidPackage}. |
| SortPriority | Entero que representa la prioridad relativa de este archivo de plantilla o asistente. Por ejemplo, si este elemento tiene un valor de 1, este elemento se muestra junto a otros elementos con un valor de 1 y antes de todos los elementos con un valor de ordenación de 2 o más.<br /><br /> La prioridad de ordenación es relativa a los elementos del mismo directorio. Puede haber más de un archivo. vsdir en el mismo directorio. En ese caso, los elementos de All <em>.</em> se combinan los archivos vsdir de ese directorio. Los elementos con la misma prioridad se muestran en el orden lexicográfico sin distinción de mayúsculas y minúsculas del nombre mostrado. La `_wcsicmp` función se usa para ordenar los elementos.<br /><br /> Los elementos no descritos en los archivos. vsdir incluyen un número de prioridad mayor que el número de prioridad más alto enumerado en los archivos. vsdir. El resultado es que estos elementos se encuentran al final de la lista mostrada, independientemente de su nombre. |
| Descripción | Descripción localizada del archivo de plantilla o del asistente. Este campo puede ser una cadena o un identificador de recursos con el formato "#ResID". Esta cadena aparece en el cuadro de diálogo **nuevo proyecto** o **Agregar nuevo elemento** cuando se selecciona el elemento. |
| DLLPath o {clsidPackage} | Se usa para cargar un icono para el archivo de plantilla o el asistente. El icono se carga como un recurso fuera de un archivo. dll o. exe mediante IconResourceId. Este archivo. dll o. exe se puede identificar mediante una ruta de acceso completa o mediante un GUID de un VSPackage. La DLL de implementación del VSPackage se usa para cargar el icono (no el archivo DLL satélite). |
| IconResourceId | El identificador de recurso en el archivo dll de implementación de DLL o VSPackage que determina el icono que se va a mostrar. |
| Marcas ( <xref:Microsoft.VisualStudio.Shell.Interop.__VSDIRFLAGS> ) | Se utiliza para deshabilitar o habilitar los campos **nombre** y **Ubicación** en el cuadro de diálogo **Agregar nuevo elemento** . El valor del campo **Flags** es el decimal equivalente a la combinación de marcadores de bits necesarios.<br /><br /> Cuando un usuario selecciona un elemento en la pestaña **nuevo** , el proyecto determina si el campo Nombre y el campo Ubicación se muestran cuando se muestra por primera vez el cuadro de diálogo **Agregar nuevo elemento** . Un elemento, a través de un archivo. vsdir, solo puede controlar si los campos están habilitados o deshabilitados cuando se selecciona el elemento. |
| SuggestedBaseName | Representa el nombre predeterminado del archivo, el asistente o la plantilla. Este campo es una cadena o un identificador de recursos con el formato "#ResID". El IDE usa este valor para proporcionar un nombre predeterminado para el elemento. Este valor base se anexa con un valor entero para que el nombre sea único, como MyFile21. asp.<br /><br /> En la lista anterior, Description, DLLPath, IconResourceId, flags y SuggestedBaseNumber se aplican únicamente a los archivos de plantilla y de asistente. Estos campos no se aplican a las carpetas. Este hecho se ilustra en el código del archivo BscPrjProjectItems en la \<EnvSDK> clave del registro \BscPrj\BscPrj\BscPrjProjectItems. Este archivo contiene tres registros (uno para cada carpeta) con cuatro campos para cada registro: RelPathName, {clsidPackage}, LocalizedName y SortPriority.<br /><br /> `General&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#110&#124;100`<br /><br /> `Source_Files&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#111&#124;110`<br /><br /> `Env&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#112&#124;120` |

 Al crear un archivo de asistente, también debe tener en cuenta los siguientes problemas.

- Los campos opcionales para los que no existen datos significativos tienen que contener un cero (0) como marcador de posición.

- Si no se proporciona ningún nombre traducido, se utiliza el nombre de la ruta de acceso relativa en el archivo del asistente.

- DLLPath invalida clsidPackage para la ubicación del icono.

- Si no se define ningún icono, el IDE sustituye el icono predeterminado de un archivo que tiene esa extensión.

- Si no se proporciona ningún nombre base sugerido, se utiliza ' proyecto '.

- Si elimina los archivos. vsz, las carpetas o los archivos de plantilla, también debe quitar los registros asociados del archivo. vsdir.

## <a name="see-also"></a>Consulte también
- [Asistentes](../../extensibility/internals/wizards.md)
- [Archivo de asistente (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
