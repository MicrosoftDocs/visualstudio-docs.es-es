---
title: Registrando generadores de archivo único | Microsoft Docs
description: Obtenga información sobre cómo registrar una herramienta personalizada en Visual Studio para crear una instancia de ella y asociarla a un tipo de proyecto determinado.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, custom tools
- custom tools, defining registry settings
ms.assetid: db7592c0-1273-4843-9617-6e2ddabb6ca8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ee110defb06d308c017230a36cebc2b04b3c63b9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105062686"
---
# <a name="registering-single-file-generators"></a>Registro de generadores de un solo archivo
Para que una herramienta personalizada esté disponible en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , debe registrarla de modo que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pueda crear una instancia de ella y asociarla a un tipo de proyecto determinado.

### <a name="to-register-a-custom-tool"></a>Para registrar una herramienta personalizada

1. Registre el archivo DLL de la herramienta personalizada en el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] registro local o en el registro del sistema, en HKEY_CLASSES_ROOT.

    Por ejemplo, esta es la información de registro de la herramienta personalizada MSDataSetGenerator administrada, que se incluye en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] :

   ```
   [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\CLSID\{E76D53CC-3D4F-40A2-BD4D-4F3419755476}]
   @="COM+ class: Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"
   "InprocServer32"="C:\\WINDOWS\\system32\\mscoree.dll"
   "ThreadingModel"="Both"
   "Class"="Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"
   "Assembly"="Microsoft.VSDesigner, Version=14.0.0.0, Culture=Neutral, PublicKeyToken=b03f5f7f11d50a3a"
   ```

2. Cree una clave del registro en el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] subárbol deseado en \\ *GUID* de generadores, donde *GUID* es el GUID definido por el sistema o servicio del proyecto del lenguaje específico. El nombre de la clave se convierte en el nombre de programación de la herramienta personalizada. La clave de herramienta personalizada tiene los siguientes valores:

   - (Es el valor predeterminado).

        Opcional. Proporciona una descripción descriptiva de la herramienta personalizada. Este parámetro es opcional, pero se recomienda.

   - CLSID

        Necesario. Especifica el identificador de la biblioteca de clases del componente COM que implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> .

   - GeneratesDesignTimeSource

        Necesario. Indica si los tipos de los archivos generados por esta herramienta personalizada se ponen a disposición de los diseñadores visuales. El valor de este parámetro debe ser (cero) 0 para los tipos que no están disponibles para los diseñadores visuales o (uno) 1 para los tipos disponibles para los diseñadores visuales.

   > [!NOTE]
   > Debe registrar la herramienta personalizada por separado para cada idioma para el que desee que la herramienta personalizada esté disponible.

    Por ejemplo, el MSDataSetGenerator se registra una vez por cada idioma:

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

## <a name="see-also"></a>Consulte también
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>
- [Implementación de generadores de un solo archivo](../../extensibility/internals/implementing-single-file-generators.md)
- [Exposición de tipos a diseñadores visuales](../../extensibility/internals/exposing-types-to-visual-designers.md)
- [Introducción al objeto BuildManager](/previous-versions/8f9kffa8(v=vs.140))