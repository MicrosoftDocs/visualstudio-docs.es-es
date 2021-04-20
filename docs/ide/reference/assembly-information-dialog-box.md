---
title: Información de ensamblado (Cuadro de diálogo)
description: Aprenda sobre el cuadro de diálogo Información de ensamblado y cómo se utiliza para especificar los valores de los atributos de ensamblado globales de .NET Framework.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesAssemblyInfo
helpviewer_keywords:
- Assembly Information dialog box
ms.assetid: 8f1f6449-e03d-4a5b-9076-d3b1f84ada48
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0a8f4d5612fe8ceaa4470f441133767178b119cc
ms.sourcegitcommit: 6d88913a8b5a9e5eda01d3f95205b4d138f440f8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/13/2021
ms.locfileid: "107295447"
---
# <a name="assembly-information-dialog-box"></a>Cuadro de diálogo Información de ensamblado

El cuadro de diálogo Información de ensamblado se usa para especificar los valores de los atributos de ensamblado globales de .NET Framework, que se almacenan en el archivo AssemblyInfo creado automáticamente con el proyecto. En el Explorador de soluciones, el archivo AssemblyInfo se encuentra en el nodo **Mi proyecto** de los proyectos de Visual Basic (haga clic en **Mostrar todos los archivos** para verlo). En el caso de los proyectos de C#, se encuentra en **Propiedades**. Para más información, consulte [Atributos (C#)](/dotnet/csharp/programming-guide/concepts/attributes/index).

Para acceder a este cuadro de diálogo, seleccione un nodo de proyecto en el **Explorador de soluciones** y después, en el menú **Proyecto**, seleccione **Propiedades**. En la página **Aplicación**, seleccione el botón **Información de ensamblado**.

## <a name="uielement-list"></a>Lista de UIElement

**Título**\
Especifica un título para el manifiesto del ensamblado. Se corresponde con <xref:System.Reflection.AssemblyTitleAttribute>.

**Descripción**\
Especifica una descripción opcional para el manifiesto del ensamblado. Se corresponde con <xref:System.Reflection.AssemblyDescriptionAttribute>.

**Empresa**\
Especifica un nombre de empresa para el manifiesto del ensamblado. Se corresponde con <xref:System.Reflection.AssemblyCompanyAttribute>.

Puede establecer o cambiar el valor predeterminado para Empresa en el Registro. Busque el valor **RegisteredOrganization** en la clave **Computer\HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\Windows NT\CurrentVersion** o en la clave **Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion**, dependiendo de su versión de Windows.

**Producto**\
Especifica un nombre de producto para el manifiesto del ensamblado. Se corresponde con <xref:System.Reflection.AssemblyProductAttribute>.

**Copyright**\
Especifica un aviso de copyright para el manifiesto del ensamblado. Se corresponde con <xref:System.Reflection.AssemblyCopyrightAttribute>.

**Marca comercial**\
Especifica una marca comercial para el manifiesto del ensamblado. Se corresponde con <xref:System.Reflection.AssemblyTrademarkAttribute>.

**Versión de ensamblado**\
Especifica la versión del ensamblado. Se corresponde con <xref:System.Reflection.AssemblyVersionAttribute>.

**Versión de archivo**\
Especifica un número de versión que indica al compilador que use una versión específica para el recurso de versión de archivo Win32. Se corresponde con <xref:System.Reflection.AssemblyFileVersionAttribute>.

**GUID**\
Un GUID único que identifica el ensamblado. Al crear un proyecto, Visual Studio genera un GUID para el ensamblado. Se corresponde con <xref:System.Guid>.

**Idioma neutro**\
Especifica la cultura que admite el ensamblado. Se corresponde con <xref:System.Resources.NeutralResourcesLanguageAttribute>. El valor predeterminado es **(None)** .

**Crear ensamblado visible a través de COM**\
Especifica si los tipos del ensamblado estarán disponibles para COM. Se corresponde con <xref:System.Runtime.InteropServices.ComVisibleAttribute>.

> [!NOTE]
> Para más información sobre cómo establecer estas propiedades al generar un paquete NuGet en una biblioteca de clases de .NET Framework, consulte [Configurar las propiedades del proyecto para el paquete](/nuget/quickstart/create-and-publish-a-package-using-visual-studio-net-framework#configure-project-properties-for-the-package). Y para obtener más información sobre licencias y expresiones relacionadas con un paquete NuGet, consulte [licenses.nuget.org](/nuget/nuget-org/licenses.nuget.org/).

## <a name="see-also"></a>Consulte también

- [Página de aplicación, Diseñador de proyectos (Visual Basic)](../../ide/reference/application-page-project-designer-visual-basic.md)
- [Atributos](/previous-versions/z0w1kczw(v=vs.140))