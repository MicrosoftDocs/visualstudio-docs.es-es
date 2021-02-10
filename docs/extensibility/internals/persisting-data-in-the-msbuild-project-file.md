---
title: Almacenar datos en el archivo de proyecto de MSBuild | Microsoft Docs
description: Obtenga información sobre cómo conservar los datos en un archivo de proyecto y usar IPersistXMLFragment para mantener los datos en el archivo de proyecto a través de los niveles de agregación de subtipos de proyecto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project files, persisting data in
ms.assetid: 6a920cb7-453d-4ffd-af1c-6f3084bd03f7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d2011cd8686f3210ee534fdaefaa26d2f3b4ad5e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99954454"
---
# <a name="persisting-data-in-the-msbuild-project-file"></a>Conservación de datos en el archivo de proyecto de MSBuild
Un subtipo de proyecto puede necesitar conservar los datos específicos del subtipo en el archivo de proyecto para su uso posterior. Un subtipo de proyecto usa la persistencia del archivo de proyecto para cumplir los siguientes requisitos:

1. Conservar los datos utilizados como parte de la compilación del proyecto. (Para obtener más información sobre el Microsoft Build Engine, vea [msbuild](../../msbuild/msbuild.md)). La información relacionada con la compilación puede:

    1. Datos independientes de la configuración. Es decir, los datos almacenados en elementos de MSBuild con condiciones en blanco o que faltan.

    2. Datos dependientes de la configuración. Es decir, los datos almacenados en elementos de MSBuild que están acondicionados para una configuración de proyecto determinada. Por ejemplo:

        ```
        <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">
        ```

2. Conservar los datos que no son relevantes para la compilación. Estos datos se pueden expresar en XML de forma libre que no se validan con respecto a un esquema XML.

    1. Datos independientes de la configuración.

    2. Datos dependientes de la configuración.

## <a name="persisting-build-related-information"></a>Almacenar información de Build-Related
 La persistencia de los datos resulta útil para compilar un proyecto de se controla a través de MSBuild. El sistema MSBuild mantiene una tabla maestra de información relacionada con la compilación. Los subtipos de proyecto son responsables de obtener acceso a estos datos para obtener y establecer los valores de propiedad. Los subtipos de proyecto también pueden aumentar la tabla de datos relacionada con la compilación agregando propiedades adicionales que se van a conservar y quitando las propiedades para que no se conserven.

 Para modificar los datos de MSBuild, un subtipo de proyecto es responsable de recuperar el objeto de propiedad de MSBuild del sistema de proyecto base a través de <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> . <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> es una interfaz implementada en el sistema de proyectos principal y las consultas de subtipo de proyecto agregado para ella mediante la ejecución de `QueryInterface` .

 En el procedimiento siguiente se describen los pasos para quitar una propiedad mediante <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> .

#### <a name="to-remove-a-property-from-an-msbuild-project-file"></a>Para quitar una propiedad de un archivo de proyecto de MSBuild

1. Llame a `QueryInterface` en <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> del subtipo de proyecto.

2. Llame a <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.RemoveProperty%2A> con `pszPropName` establecido en la propiedad que desea quitar.

### <a name="persisting-non-build-related-information"></a>Conservar información relacionada que no sea de compilación
 La persistencia de los datos de los archivos de proyecto que no importan a la compilación se controla a través de <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> .

 Puede implementar <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> en el objeto principal `project subtype aggregator` , el `project subtype project configuration` objeto o ambos.

 Los puntos siguientes describen los conceptos principales relacionados con la persistencia de la información relacionada con la no compilación.

- El proyecto base llama a en el subtipo de proyecto principal (es decir, el subtipo de proyecto más externo) para cargar y guardar datos independientes de la configuración y llama a los objetos de configuración de proyecto de subtipo de proyecto para cargar o guardar los datos dependientes de la configuración.

- El proyecto base llama a los métodos de <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> varias veces para cada nivel de agregación de subtipos de proyecto y pasa el GUID para cada nivel.

- El proyecto base pasa o recibe un fragmento XML dedicado a un subtipo de proyecto determinado y utiliza este mecanismo como una forma de conservar el estado entre los niveles de agregación.

- El proyecto base llama a la implementación del subtipo de proyecto más exterior <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> pasando un GUID. Si el GUID pertenece al subtipo de proyecto más externo, controla la propia llamada; en caso contrario, delega la llamada a un subtipo de proyecto interno, y así sucesivamente, hasta que se encuentra el subtipo de proyecto al que corresponde el GUID.

- Un subtipo de proyecto también puede modificar el fragmento XML antes o después de delegar la llamada a un subtipo de proyecto interno. En el ejemplo siguiente se muestra un extracto de un archivo de proyecto, donde el nombre de un archivo que contiene las propiedades específicas de un subtipo de proyecto, se pasa a ese subtipo de proyecto.

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
