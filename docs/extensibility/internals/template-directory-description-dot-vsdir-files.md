---
title: Descripción del directorio de plantillas (. Vsdir) Archivos de la casa de la ciudad ( Vsdir) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .vsdir files
- VSDIR files
- template directory description files
ms.assetid: 9df51800-190e-4662-b685-fdaafcff1400
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 16ba609d5b05d565a12b38bd19e9a777851ced5b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704685"
---
# <a name="template-directory-description-vsdir-files"></a>Archivos de descripción del directorio de plantilla (.Vsdir)
Un archivo de descripción de directorio de plantilla (.vsdir) es un archivo de texto que permite al entorno de desarrollo integrado (IDE) mostrar carpetas, archivos .vsz del asistente y archivos de plantilla asociados al proyecto en cuadros de diálogo. El contenido incluye un registro por archivo o carpeta. Todos los archivos .vsdir en una ubicación a la que se hace referencia se combinan, aunque generalmente solo se proporciona un archivo .vsdir para describir varias carpetas, asistentes o archivos de plantilla.

 Las carpetas (subdirectorios), los archivos a los que se hace referencia en el archivo .vsdir y el propio archivo .vsdir se encuentran en el mismo directorio. Cuando el IDE ejecuta un asistente o muestra una carpeta o un archivo en los cuadros de diálogo **Nuevo proyecto** o Agregar **nuevo elemento,** el IDE examina el directorio que contiene los archivos ejecutados para determinar si hay un archivo .vsdir presente. Si se encuentra un archivo .vsdir, el IDE lo lee para determinar si contiene una entrada para la carpeta o archivo ejecutado o mostrado. Si se encuentra una entrada, el IDE usa la información en la ejecución del asistente o la visualización del contenido.

 El ejemplo de código siguiente procede del archivo \<SourceFiles.vsdir de la clave del Registro EnvSDK>, BscPrj, BscPrj, BscPrjProjectItems, Source_Files:

```
HeaderFile.h|{E59935A1-6156-11d1-87A6-00A0C91E2A46}|#125|130|#126|0|0|0|#127
SourceFile.cpp|{E59935A1-6156-11d1-87A6-00A0C91E2A46}|#122|110|#123|0|0|0|#124
```

 En este caso, dos registros están en un archivo. Una nueva línea (carácter de retorno de carro) separa cada registro. Cada línea representa un tipo de archivo diferente. Un carácter de tubería (&#124;) separa los campos de cada registro. Un único directorio puede contener varios archivos .vsdir que tienen nombres de archivo diferentes, o puede tener un archivo .vsdir para cada tipo de archivo.

## <a name="fields"></a>Fields
 En la tabla siguiente se enumeran los campos especificados para cada registro.

| Campo | Descripción |
| - | - |
| Nombre relativo de ruta de acceso (RelPathName) | El nombre de la carpeta, plantilla o archivo .vsz, como HeaderFile.h o MyWizard.vsz. Este campo también puede ser un nombre utilizado para representar una carpeta. |
| {clsidPackage} | GUID del VSPackage que permite el acceso a cadenas localizadas, como LocalizedName, Description, IconResourceId y SuggestedBaseName, en los recursos de la biblioteca de vínculos dinámicos por satélite (DLL) del VSPackage. IconResourceId se aplica si DLLPath no se proporciona. **Nota:**  Este campo es opcional a menos que uno o varios de los campos anteriores sea un identificador de recursos. Este campo suele estar en blanco para los archivos .vsdir que se corresponden con asistentes de terceros que no localizan su texto. |
| LocalizedName | El nombre localizado del archivo de plantilla o asistente. Este campo puede ser una cadena o un identificador de recurso con el formato "#ResID". Este nombre se muestra en el cuadro de diálogo **Agregar nuevo elemento.** **Nota:**  Si LocalizedName es un identificador de recurso, se requiere el valor de .clsidPackage. |
| SortPriority | Entero que representa la prioridad relativa de este archivo de plantilla o asistente. Por ejemplo, si este elemento tiene un valor de 1, este elemento se muestra junto a otros elementos con un valor de 1 y por delante de todos los elementos con un valor de ordenación de 2 o mayor.<br /><br /> La prioridad de ordenación es relativa a los elementos del mismo directorio. Puede haber más de un archivo .vsdir en el mismo directorio. En ese caso, los elementos de todos los <em>archivos .</em> vsdir archivos en ese directorio se combinan. Los elementos con la misma prioridad se enumeran en orden lexicográfico que no distingue mayúsculas de minúsculas del nombre mostrado. La `_wcsicmp` función se utiliza para ordenar los artículos.<br /><br /> Los elementos no descritos en los archivos .vsdir incluyen un número de prioridad mayor que el número de prioridad más alto que aparece en los archivos .vsdir. El resultado es que estos elementos están al final de la lista mostrada independientemente de su nombre. |
| Descripción | La descripción localizada del archivo de plantilla o asistente. Este campo puede ser una cadena o un identificador de recurso con el formato "#ResID". Esta cadena aparece en el cuadro de diálogo **Nuevo proyecto** o Agregar **nuevo elemento** cuando se selecciona el elemento. |
| DLLPath o {clsidPackage} | Se utiliza para cargar un icono para el archivo de plantilla o el asistente. El icono se carga como un recurso de un archivo .dll o .exe mediante el IconResourceId. Este archivo .dll o .exe se puede identificar mediante una ruta de acceso completa o mediante un GUID de un VSPackage. El archivo DLL de implementación del VSPackage se utiliza para cargar el icono (no el archivo DLL satélite). |
| IconResourceId | Identificador de recursos en el archivo DLL de implementación de DLL o VSPackage que determina el icono que se va a mostrar. |
| Banderas<xref:Microsoft.VisualStudio.Shell.Interop.__VSDIRFLAGS>( ) | Se utiliza para deshabilitar o habilitar los campos **Nombre** y **Ubicación** en el cuadro de diálogo **Agregar nuevo elemento.** El valor del campo **Flags** es el equivalente decimal de la combinación de indicadores de bits necesarios.<br /><br /> Cuando un usuario selecciona un elemento en la ficha **Nuevo,** el proyecto determina si el campo Nombre y el campo Ubicación se muestran cuando se muestra por primera vez el cuadro de diálogo **Agregar nuevo elemento.** Un elemento, a través de un archivo .vsdir, solo puede controlar si los campos están habilitados frente a deshabilitados cuando se selecciona el elemento. |
| SuggestedBaseName | Representa el nombre predeterminado para el archivo, asistente o plantilla. Este campo es una cadena o un identificador de recurso con el formato "#ResID". El IDE usa este valor para proporcionar un nombre predeterminado para el elemento. Este valor base se anexa con un valor entero para que el nombre sea único, como MyFile21.asp.<br /><br /> En la lista anterior, Description, DLLPath, IconResourceId, Flags y SuggestedBaseNumber solo se aplican a los archivos de plantilla y asistente. Estos campos no se aplican a las carpetas. Este hecho se ilustra en el código del archivo \<BscPrjProjectItems de la clave del Registro EnvSDK>,BscPrj, BscPrj y BscPrjProjectItems. Este archivo contiene tres registros (uno para cada carpeta) con cuatro campos para cada registro: RelPathName, .clsidPackage, LocalizedName y SortPriority.<br /><br /> `General&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#110&#124;100`<br /><br /> `Source_Files&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#111&#124;110`<br /><br /> `Env&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#112&#124;120` |

 Al crear un archivo de asistente, también debe tener en cuenta los siguientes problemas.

- Los campos opcionales para los que no existen datos significativos tienen que contener un cero (0) como marcador de posición.

- Si no se proporciona ningún nombre localizado, el nombre de ruta de acceso relativo se utiliza en el archivo del asistente.

- DLLPath reemplaza clsidPackage para la ubicación del icono.

- Si no se define ningún icono, el IDE sustituye el icono predeterminado por un archivo que tiene esa extensión.

- Si no se proporciona ningún nombre base sugerido, se utiliza 'Proyecto'.

- Si elimina los archivos, carpetas o archivos de plantilla .vsz, también debe quitar sus registros asociados del archivo .vsdir.

## <a name="see-also"></a>Vea también
- [Asistentes](../../extensibility/internals/wizards.md)
- [Archivo de asistente (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
