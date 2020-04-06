---
title: Registro de generadores de un solo archivo ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, custom tools
- custom tools, defining registry settings
ms.assetid: db7592c0-1273-4843-9617-6e2ddabb6ca8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1cea2ebba4739695393447a36e9842ade1670954
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705814"
---
# <a name="registering-single-file-generators"></a>Registro de generadores de un solo archivo
Para que una herramienta [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]personalizada esté disponible [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] en , debe registrarla para poder crear instancias y asociarla a un tipo de proyecto determinado.

### <a name="to-register-a-custom-tool"></a>Para registrar una herramienta personalizada

1. Registre el archivo DLL [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] de la herramienta personalizada en el registro local o en el registro del sistema, en HKEY_CLASSES_ROOT.

    Por ejemplo, aquí está la información de registro para la herramienta [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]personalizada administrada MSDataSetGenerator, que viene con:

   ```
   [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\CLSID\{E76D53CC-3D4F-40A2-BD4D-4F3419755476}]
   @="COM+ class: Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"
   "InprocServer32"="C:\\WINDOWS\\system32\\mscoree.dll"
   "ThreadingModel"="Both"
   "Class"="Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"
   "Assembly"="Microsoft.VSDesigner, Version=14.0.0.0, Culture=Neutral, PublicKeyToken=b03f5f7f11d50a3a"
   ```

2. Cree una clave del [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Registro en\\el subárbol deseado en*el GUID* de generadores, donde *GUID* es el GUID definido por el sistema de proyecto o servicio del lenguaje específico. El nombre de la clave se convierte en el nombre de programación de la herramienta personalizada. La clave de herramienta personalizada tiene los siguientes valores:

   - (Es el valor predeterminado).

        Opcional. Proporciona una descripción fácil de usar de la herramienta personalizada. Este parámetro es opcional, pero se recomienda.

   - CLSID

        Necesario. Especifica el identificador de la biblioteca de clases <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>del componente COM que implementa .

   - GeneratesDesignTimeSource

        Necesario. Indica si los tipos de archivos generados por esta herramienta personalizada están disponibles para los diseñadores visuales. El valor de este parámetro debe ser (cero) 0 para los tipos que no están disponibles para los diseñadores visuales o (uno) 1 para los tipos disponibles para los diseñadores visuales.

   > [!NOTE]
   > Debe registrar la herramienta personalizada por separado para cada idioma para el que desea que la herramienta personalizada esté disponible.

    Por ejemplo, MSDataSetGenerator se registra una vez para cada idioma:

   ```
   [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\Generators\{164b10b9-b200-11d0-8c61-00a0c91e29d5}\MSDataSetGenerator]
   @="Microsoft VB Code Generator for XSD"
   "CLSID"="{E76D53CC-3D4F-40a2-BD4D-4F3419755476}"
   "GeneratesDesignTimeSource"=dword:00000001

   [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\Generators\{fae04ec1-301f-11d3-bf4b-00c04f79efbc}\MSDataSetGenerator]
   @="Microsoft C# Code Generator for XSD"
   "CLSID"="{E76D53CC-3D4F-40a2-BD4D-4F3419755476}"
   "GeneratesDesignTimeSource"=dword:00000001
   ```

## <a name="see-also"></a>Vea también
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>
- [Implementación de generadores de un solo archivo](../../extensibility/internals/implementing-single-file-generators.md)
- [Exposición de tipos a diseñadores visuales](../../extensibility/internals/exposing-types-to-visual-designers.md)
- [Introducción al objeto BuildManager](https://msdn.microsoft.com/library/50080ec2-c1c9-412c-98ef-18d7f895e7fa)
