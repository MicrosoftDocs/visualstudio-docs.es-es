---
title: Registrar generadores de un único archivo | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- registration, custom tools
- custom tools, defining registry settings
ms.assetid: db7592c0-1273-4843-9617-6e2ddabb6ca8
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8e601b3fcf8bd702c1bc6cde427766d0f107e6bd
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51780989"
---
# <a name="registering-single-file-generators"></a>Registro de generadores de un solo archivo
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Para que estén disponibles en una herramienta personalizada [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], debe registrar tan [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] puede inicializarla y lo asocia con un tipo de proyecto determinado.  
  
### <a name="to-register-a-custom-tool"></a>Para registrar una herramienta personalizada  
  
1.  Registrar la DLL de la herramienta personalizada o en el [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] registro local o en el registro del sistema, en HKEY_CLASSES_ROOT.  
  
     Por ejemplo, esta es la información de registro para la herramienta personalizada de MSDataSetGenerator administrada, que se incluye con [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]:  
  
    ```  
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\CLSID\{E76D53CC-3D4F-40A2-BD4D-4F3419755476}]  
    @="COM+ class: Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"  
    "InprocServer32"="C:\\WINDOWS\\system32\\mscoree.dll"  
    "ThreadingModel"="Both"  
    "Class"="Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"  
    "Assembly"="Microsoft.VSDesigner, Version=14.0.0.0, Culture=Neutral, PublicKeyToken=b03f5f7f11d50a3a"  
    ```  
  
2.  Crear una clave del registro en deseado [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] hive en generadores\\*GUID* donde *GUID* es el GUID definido por el sistema del proyecto o el servicio de lenguaje específico. El nombre de la clave se convierte en el nombre de programación de la herramienta personalizada. La clave de la herramienta personalizada tiene los siguientes valores:  
  
    -   (Predeterminado)  
  
         Opcional. Proporciona una descripción fácil de usar de la herramienta personalizada. Este parámetro es opcional pero recomendado.  
  
    -   CLSID  
  
         Requerido. Especifica el identificador de la biblioteca de clases del componente COM que implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>.  
  
    -   GeneratesDesignTimeSource  
  
         Requerido. Indica si los tipos de los archivos generados por esta herramienta personalizada están disponibles para los diseñadores visuales. El valor de este parámetro debe ser (cero) 0 para tipos no están disponibles para los diseñadores visuales o 1 (uno) para los tipos disponibles para los diseñadores visuales.  
  
    > [!NOTE]
    >  Debe registrar la herramienta personalizada por separado para cada idioma para el que desea que la herramienta personalizada esté disponible.  
  
     Por ejemplo, el MSDataSetGenerator registra a sí mismo una vez para cada idioma:  
  
    ```  
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\Generators\{164b10b9-b200-11d0-8c61-00a0c91e29d5}\MSDataSetGenerator]  
    @="Microsoft VB Code Generator for XSD"  
    "CLSID"="{E76D53CC-3D4F-40a2-BD4D-4F3419755476}"  
    "GeneratesDesignTimeSource"=dword:00000001  
  
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\Generators\{fae04ec1-301f-11d3-bf4b-00c04f79efbc}\MSDataSetGenerator]  
    @="Microsoft C# Code Generator for XSD"  
    "CLSID"="{E76D53CC-3D4F-40a2-BD4D-4F3419755476}"  
    "GeneratesDesignTimeSource"=dword:00000001  
  
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\Generators\{e6fdf8b0-f3d1-11d4-8576-0002a516ece8}\MSDataSetGenerator]  
    @="Microsoft J# Code Generator for XSD"  
    "CLSID"="{E76D53CC-3D4F-40a2-BD4D-4F3419755476}"  
    "GeneratesDesignTimeSource"=dword:00000001  
    ```  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>   
 [Implementar generadores de un solo archivo](../../extensibility/internals/implementing-single-file-generators.md)   
 [Determinar el Namespace predeterminado de un proyecto](../../misc/determining-the-default-namespace-of-a-project.md)   
 [Exposición de tipos a los diseñadores visuales](../../extensibility/internals/exposing-types-to-visual-designers.md)   
 [Introducción al objeto BuildManager](http://msdn.microsoft.com/en-us/50080ec2-c1c9-412c-98ef-18d7f895e7fa)

