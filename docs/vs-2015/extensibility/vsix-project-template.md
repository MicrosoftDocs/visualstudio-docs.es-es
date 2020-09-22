---
title: Plantilla de proyecto de VSIX | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- deploy packages
- publish extension
ms.assetid: b6c82167-e2a5-4cff-8c8b-2d72e2a9092c
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2386f1be805f6347fc32fba4ee8bfe57c8602329
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90843150"
---
# <a name="vsix-project-template"></a>Plantilla de proyecto de VSIX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede usar la plantilla de Proyecto VSIX para incluir una o varias extensiones de Visual Studio en un proyecto VSIX y, a continuación, publicar el paquete en el sitio web de [Visual Studio Marketplace](https://marketplace.visualstudio.com/) .  
  
 La implementación de VSIX admite VSPackages, ensamblados, componentes de MEF, plantillas de proyecto, plantillas de elementos, controles del cuadro de herramientas y tipos de extensión personalizados.  
  
> [!NOTE]
> Para usar proyectos VSIX, debe instalar el SDK de Visual Studio. Para obtener más información sobre el SDK de Visual Studio, vea [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="where-to-find-the-vsix-project-template"></a>Dónde encontrar la plantilla de proyecto de VSIX  
 La plantilla de Proyecto VSIX está disponible en el cuadro de diálogo **nuevo proyecto** . Expanda el nodo **Visual Basic** o el nodo **Visual C#** y, a continuación, elija **extensibilidad**.  
  
> [!TIP]
> Debe asegurarse de que se especifica .NET Framework 4,5 o una versión superior en la lista desplegable de la parte superior del cuadro de diálogo **nuevo proyecto** .  
  
## <a name="uses-of-the-vsix-project-template"></a>Usos de la plantilla de proyecto de VSIX  
 La plantilla de Proyecto VSIX tiene dos usos principales:  
  
- Para implementar plantillas de proyecto, plantillas de elementos y otras extensiones que aún no tienen compatibilidad con VSIX.  
  
- Para ajustar las salidas de varias extensiones en un paquete de implementación.  
  
  No es necesario usar la plantilla de Proyecto VSIX para implementar VSPackages u otros tipos de extensiones que ya tienen compatibilidad con VSIX.  
  
## <a name="packaging-an-extension-in-an-empty-vsix-project"></a>Empaquetar una extensión en un proyecto VSIX vacío  
 Puede empaquetar una extensión existente o una extensión que no tenga compatibilidad con VSIX, ajustándola a un proyecto VSIX vacío. La extensión que se va a ajustar debe ser de un tipo compatible con el [esquema VSIX](../extensibility/vsix-extension-schema-2-0-reference.md).  
  
#### <a name="to-package-an-extension-by-using-a-vsix-project"></a>Para empaquetar una extensión mediante un proyecto VSIX  
  
1. Cree los proyectos que componen la extensión.  
  
2. Cree un proyecto VSIX mediante la plantilla de **Proyecto VSIX** .  
  
     Source. Extension. vsixmanifest se abre en el **Diseñador de manifiestos**.  
  
3. En la pestaña **activos** , elija el botón **nuevo** .  
  
     Aparecerá el cuadro de diálogo **Agregar nuevo activo** .  
  
4. En la lista **tipo** , elija el tipo de extensión que se va a agregar.  
  
5. Para agregar una extensión o un elemento de contenido que se incluye en la solución actual (por ejemplo, una plantilla de elemento o un ensamblado compilado), realice los pasos siguientes:  
  
    1. En la lista **origen** , elija **un proyecto en la solución actual**.  
  
    2. En la lista **proyecto** , elija el nombre de la extensión.  
  
    3. En el cuadro **Insertar en esta carpeta** , escriba el nombre de una carpeta en la que se va a insertar el recurso y, a continuación, elija el botón **Aceptar** .  
  
6. Para agregar una extensión o un elemento de contenido que no esté incluido en la solución actual, realice los pasos siguientes:  
  
    1. En el cuadro de lista **origen** , elija **archivo en sistema de archivos**.  
  
    2. En el campo **ruta de acceso** , escriba la ruta de acceso completa al archivo de extensión compilado o comprimido, o use el botón **examinar** para buscar el archivo.  
  
    3. En el cuadro **Insertar en esta carpeta** , escriba el nombre de una carpeta en la que se va a insertar el recurso y, a continuación, elija el botón **Aceptar** .  
  
7. Si desea que el paquete incluya extensiones adicionales, agréguelas de la misma manera.  
  
8. Compile la solución.  
  
     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] compila un archivo. vsix que contiene un archivo de manifiesto VSIX, un archivo [Content_Types]. XML y todos los recursos de extensión que ha agregado al proyecto.  
  
## <a name="see-also"></a>Consulte también  
 [Referencia del esquema de extensión VSIX 2,0](../extensibility/vsix-extension-schema-2-0-reference.md)   
 [Buscar y usar extensiones de Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)
