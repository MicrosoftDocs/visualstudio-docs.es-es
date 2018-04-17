---
title: Descripción de directorio de la plantilla (. Archivos VSDir) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- .vsdir files
- VSDIR files
- template directory description files
ms.assetid: 9df51800-190e-4662-b685-fdaafcff1400
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 14ea2e0bcc11324e6529c70c04c11874ec4a3399
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="template-directory-description-vsdir-files"></a>Descripción de directorio de la plantilla (. Archivos VSDir)
Un archivo de descripción del directorio de plantilla (.vsdir) es un archivo de texto que permite que el entorno de desarrollo integrado (IDE) para mostrar las carpetas, archivos .vsz del asistente y archivos de plantilla que están asociados con el proyecto en cuadros de diálogo. El contenido incluye un registro por cada archivo o carpeta. Se combinan todos los archivos .vsdir en una ubicación que se hace referencia, aunque generalmente se proporciona un único archivo para describir varias carpetas, los asistentes o los archivos de plantilla.  
  
 Las carpetas (en los subdirectorios), archivos que se hace referencia en el archivo y el propio archivo .vsdir se encuentran en el mismo directorio. Cuando el IDE ejecuta un asistente o muestra una carpeta o archivo en el **nuevo proyecto** o **Agregar nuevo elemento** cuadros de diálogo, el IDE examina el directorio que contiene los archivos ejecutados para determinar si es un archivo. está presente. Si se encuentra un archivo, el IDE lo lee para determinar si contiene una entrada para el archivo o carpeta ejecutada o mostrada. Si se encuentra una entrada, el IDE usa la información de la ejecución del asistente o presentación del contenido.  
  
 El siguiente ejemplo de código pertenece al archivo SourceFiles.vsdir en el \<EnvSDK > \BscPrj\BscPrj\BscPrjProjectItems\Source_Files clave de registro:  
  
```  
HeaderFile.h|{E59935A1-6156-11d1-87A6-00A0C91E2A46}|#125|130|#126|0|0|0|#127  
SourceFile.cpp|{E59935A1-6156-11d1-87A6-00A0C91E2A46}|#122|110|#123|0|0|0|#124  
```  
  
 En este caso, dos registros se encuentran en un archivo. Una nueva línea (carácter de retorno de carro) separa cada registro. Cada línea representa un tipo de archivo diferente. Una canalización (&#124;) carácter separa los campos de cada registro. Un único directorio puede contener varios archivos .vsdir que tienen diferentes nombres de archivo, o puede tener un archivo .vsdir para cada tipo de archivo.  
  
## <a name="fields"></a>Campos  
 En la tabla siguiente enumera los campos especificados para cada registro.  
  
|Campo|Descripción|  
|-----------|-----------------|  
|Nombre de ruta de acceso relativa (RelPathName)|El nombre del archivo .vsz, plantilla o carpeta, como HeaderFile.h o MyWizard.vsz. Este campo también puede ser un nombre que se utiliza para representar una carpeta.|  
|{clsidPackage}|El GUID del VSPackage que permite el acceso a las cadenas localizadas, como LocalizedName, descripción, IconResourceId y SuggestedBaseName, en recursos de biblioteca (DLL) de vínculos dinámicos de satélite de VSPackage. IconResourceId se aplica si no se proporciona DLLPath. **Nota:** este campo es opcional, a menos que uno o varios de los campos anteriores son un identificador de recurso. Este campo está normalmente en blanco para los archivos .vsdir que se corresponden con los asistentes para aplicaciones de terceros que no localización el texto.|  
|LocalizedName|El nombre localizado del archivo de plantilla o el asistente. Este campo puede ser una cadena o un identificador de recursos de la forma "#ResID". Este nombre se muestra en el **Agregar nuevo elemento** cuadro de diálogo. **Nota:** si LocalizedName es un identificador de recurso, es necesario {clsidPackage}.|  
|SortPriority|Un entero que representa la prioridad relativa de este archivo de plantilla o el asistente. Por ejemplo, si este elemento tiene un valor de 1, se muestra este elemento junto a otros elementos con un valor de 1 y por delante de todos los elementos con un valor de ordenación de 2 o mayor.<br /><br /> Prioridad de ordenación es relativo a los elementos en el mismo directorio. Puede haber más de un archivo en el mismo directorio. En ese caso, los elementos de todos los *.* se combinan archivos VSDir en ese directorio. Elementos con la misma prioridad se muestran en orden lexicográfico entre mayúsculas y minúsculas del nombre que se muestra. El `_wcsicmp` función se utiliza para ordenar los elementos.<br /><br /> Elementos que no se describe en los archivos .vsdir incluyen un número de prioridad mayor que el número de prioridad más alto aparece en los archivos .vsdir. El resultado es que estos elementos al final de la lista que aparece, independientemente de su nombre.|  
|Descripción|La descripción localizada del archivo de plantilla o el asistente. Este campo puede ser una cadena o un identificador de recursos de la forma "#ResID". Esta cadena aparece en la **nuevo proyecto** o **Agregar nuevo elemento** cuadro de diálogo cuando se selecciona el elemento.|  
|DLLPath o {clsidPackage}|Se usa para cargar un icono para el archivo de plantilla o el asistente. El icono se carga como un recurso fuera de un archivo .dll o .exe mediante el IconResourceId. Este archivo .dll o .exe puede identificarse mediante el uso de una ruta de acceso completa o mediante el uso de un GUID de un VSPackage. La implementación del archivo DLL del VSPackage se usa para cargar el icono (no el archivo DLL de satélite).|  
|IconResourceId|El identificador de recursos en la implementación de los archivos DLL o VSPackage DLL que determina el icono para mostrar.|  
|Marcas (<xref:Microsoft.VisualStudio.Shell.Interop.__VSDIRFLAGS>)|Usar para habilitar o deshabilitar la **nombre** y **ubicación** campos en el **Agregar nuevo elemento** cuadro de diálogo. El valor de la **marcas** campo es el equivalente decimal de la combinación de marcas de bits necesarios.<br /><br /> Cuando un usuario selecciona un elemento en el **New** ficha, el proyecto determina si el campo de nombre y el campo de ubicación se muestran cuando el **Agregar nuevo elemento** cuadro de diálogo aparece por primera vez. Un elemento a través de un archivo .vsdir, puede controlar solo si están habilitados los campos frente a deshabilitado cuando el elemento está seleccionado.|  
|SuggestedBaseName|Representa el nombre predeterminado para el archivo, el asistente o la plantilla. Este campo es una cadena o un identificador de recursos de la forma "#ResID". El IDE usa este valor para proporcionar un nombre predeterminado para el elemento. Este valor base se anexa con un valor entero para que el nombre sea único, como MyFile21.asp.<br /><br /> En la lista anterior, descripción, DLLPath, IconResourceId, marcas y SuggestedBaseNumber solo se aplican a los archivos de plantilla y el asistente. Estos campos no se aplican a las carpetas. Este hecho se ilustra en el código en el archivo BscPrjProjectItems en el \<EnvSDK > \BscPrj\BscPrj\BscPrjProjectItems clave de registro. Este archivo contiene tres registros (uno para cada carpeta) con cuatro campos para cada registro: RelPathName, {clsidPackage}, LocalizedName y SortPriority.<br /><br /> `General&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#110&#124;100`<br /><br /> `Source_Files&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#111&#124;110`<br /><br /> `Env&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#112&#124;120`|  
  
 Cuando se crea un archivo de asistente, también debe considerar lo siguiente.  
  
-   Los campos opcionales para los que no existen datos significativos tienen que contener un cero (0) como marcador de posición.  
  
-   Si no se proporciona ningún nombre localizado, el nombre de ruta de acceso relativa se utiliza en el archivo del asistente.  
  
-   DLLPath invalida clsidPackage para la ubicación del icono.  
  
-   Si no se ha definido ningún icono, el IDE sustituye el icono predeterminado para un archivo con esa extensión.  
  
-   Si no se proporciona ningún nombre de base sugerido, se utiliza 'Proyecto'.  
  
-   Si elimina los archivos .vsz, carpetas o archivos de plantilla, también debe quitar los registros asociados desde el archivo.  
  
## <a name="see-also"></a>Vea también  
 [Asistentes](../../extensibility/internals/wizards.md)   
 [Archivos de asistentes (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)