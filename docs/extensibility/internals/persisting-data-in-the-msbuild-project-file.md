---
title: Datos persistentes en el archivo de proyecto de MSBuild ( Project File) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project files, persisting data in
ms.assetid: 6a920cb7-453d-4ffd-af1c-6f3084bd03f7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e83526007f676ae94ddce57936b627bcb4308c2a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706696"
---
# <a name="persisting-data-in-the-msbuild-project-file"></a>Conservación de datos en el archivo de proyecto de MSBuild
Es posible que un subtipo de proyecto deba conservar datos específicos del subtipo en el archivo de proyecto para su uso posterior. Un subtipo de proyecto utiliza la persistencia del archivo de proyecto para cumplir los siguientes requisitos:

1. Persista los datos utilizados como parte de la creación del proyecto. (Para obtener más información sobre el motor de compilación de Microsoft, vea [MSBuild](../../msbuild/msbuild.md).) La información relacionada con la compilación puede:

    1. Datos independientes de la configuración. Es decir, datos almacenados en elementos de MSBuild con condiciones en blanco o que faltan.

    2. Datos dependientes de la configuración. Es decir, los datos almacenados en elementos de MSBuild que están condicionados para una configuración de proyecto determinada. Por ejemplo:

        ```
        <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">
        ```

2. Persista los datos que no son relevantes para compilar. Estos datos se pueden expresar en XML de forma libre que no se valida con un esquema XML.

    1. Datos independientes de la configuración.

    2. Datos dependientes de la configuración.

## <a name="persisting-build-related-information"></a>Persistir en la información relacionada con la compilación
 La persistencia de datos útiles para crear un proyecto se controla a través de MSBuild. El sistema MSBuild mantiene una tabla maestra de información relacionada con la compilación. Los subtipos de proyecto son responsables de tener acceso a estos datos para obtener y establecer valores de propiedad. Los subtipos de proyecto también pueden aumentar la tabla de datos relacionada con la compilación agregando propiedades adicionales que se conservarán y quitando las propiedades para que no se conserven.

 Para modificar los datos de MSBuild, un subtipo de proyecto es responsable de <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>recuperar el objeto de propiedad MSBuild desde el sistema del proyecto base a través de . <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>es una interfaz implementada en el sistema de proyecto principal y la `QueryInterface`agregación de consultas de subtipo de proyecto para él mediante la ejecución de .

 El siguiente procedimiento describe los pasos <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>para quitar una propiedad mediante .

#### <a name="to-remove-a-property-from-an-msbuild-project-file"></a>Para quitar una propiedad de un archivo de proyecto de MSBuild

1. Llame `QueryInterface` <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> al subtipo de proyecto.

2. Llame <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.RemoveProperty%2A> `pszPropName` con establecido en la propiedad que desea quitar.

### <a name="persisting-non-build-related-information"></a>Persistir en información relacionada con la construcción
 La persistencia de datos en archivos de proyecto <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>que no importa compilar se controla a través de .

 Puede implementar <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> en `project subtype aggregator` el objeto `project subtype project configuration` principal, el objeto o ambos.

 Los siguientes puntos describen los conceptos principales relativos a la persistencia de la información no relacionada con la compilación.

- El proyecto base llama al objeto de agregador de subtipo de proyecto principal (es decir, el subtipo de proyecto más externo) para cargar y guardar datos independientes de la configuración, y llama a los objetos de configuración del proyecto de subtipo para cargar o guardar datos dependientes de la configuración.

- El proyecto base llama <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> a los métodos de varias veces para cada nivel de agregación de subtipos de proyecto y pasa el GUID para cada nivel.

- El proyecto base pasa o recibe un fragmento XML dedicado a un subtipo de proyecto determinado y utiliza este mecanismo como una forma de conservar el estado entre los niveles de agregación.

- El proyecto base llama a la <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>implementación del subtipo de proyecto más externo pasando un GUID. Si el GUID pertenece al subtipo de proyecto más externo, controla la propia llamada; de lo contrario, delega la llamada a un subtipo de proyecto interno, y así sucesivamente, hasta que se encuentra el subtipo de proyecto al que corresponde el GUID.

- Un subtipo de proyecto también puede modificar el fragmento XML antes o después de delegar la llamada a un subtipo de proyecto interno. En el ejemplo siguiente se muestra un extracto de un archivo de proyecto, donde un nombre de un archivo que contiene propiedades específicas de un subtipo de proyecto, se pasa a ese subtipo de proyecto.

    ```
    <ProjectExtensions>
        <VisualStudio>
          <FlavorProperties GUID="{<FlavorGUID>}">
            <FlavorProject TestFileFolder="TestFile" />
          </FlavorProperties>
        </VisualStudio>
      </ProjectExtensions>
    ```

## <a name="see-also"></a>Vea también
- [Subtipos de proyecto](../../extensibility/internals/project-subtypes.md)
