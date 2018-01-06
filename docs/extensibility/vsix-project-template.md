---
title: Plantilla de proyecto VSIX | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploy packages
- publish extension
ms.assetid: b6c82167-e2a5-4cff-8c8b-2d72e2a9092c
caps.latest.revision: "21"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: de8de116a9853391249a7a37a35bd54d0a6946d2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="vsix-project-template"></a>Plantilla de proyecto VSIX
Puede utilizar la plantilla de proyecto de VSIX que incluya una o más extensiones de Visual Studio en un proyecto VSIX y, a continuación, publicar el paquete en el [Galería de Visual Studio](http://go.microsoft.com/fwlink/?LinkID=123847) sitio Web.  
  
 Implementación de VSIX admite VSPackages, ensamblados, componentes MEF, plantillas de proyecto, plantillas de elementos, controles de cuadro de herramientas y tipos de extensión personalizados.  
  
> [!NOTE]
>  Para usar proyectos VSIX, debe instalar el SDK de Visual Studio. Para obtener más información sobre el SDK de Visual Studio, vea [SDK de Visual Studio](../extensibility/visual-studio-sdk.md).  
  
## <a name="where-to-find-the-vsix-project-template"></a>Dónde encontrar la plantilla de proyecto VSIX  
 La plantilla de proyecto VSIX está disponible en la **nuevo proyecto** cuadro de diálogo. Expanda el **Visual Basic** nodo o la **Visual C#** nodo y, a continuación, elija **extensibilidad**.  
  
> [!TIP]
>  Debe asegurarse de que .NET Framework 4.5 o versiones posteriores, se especifica en la lista desplegable en la parte superior de la **nuevo proyecto** cuadro de diálogo.  
  
## <a name="uses-of-the-vsix-project-template"></a>Usos de la plantilla de proyecto VSIX  
 La plantilla de proyecto VSIX tiene dos usos principales:  
  
-   Para implementar plantillas de proyecto, plantillas de elementos y otras extensiones que aún no dispone de soporte técnico VSIX.  
  
-   Para ajustar las salidas de varias extensiones en un paquete de distribución.  
  
 No es necesario usar la plantilla de proyecto de VSIX para implementar paquetes VSPackage u otros tipos de extensiones que ya tienen VSIX admite.  
  
## <a name="packaging-an-extension-in-an-empty-vsix-project"></a>Empaquetar una extensión en un proyecto VSIX vacío  
 Puede empaquetar una extensión existente o una extensión que no tenga ya VSIX admite incluyéndolo en un proyecto VSIX vacío. La extensión que se va a encapsular debe ser de un tipo que sea compatible con la [esquema VSIX](../extensibility/vsix-extension-schema-2-0-reference.md).  
  
#### <a name="to-package-an-extension-by-using-a-vsix-project"></a>Para empaquetar una extensión utilizando un proyecto VSIX  
  
1.  Compile los proyectos que forman la extensión.  
  
2.  Crear un proyecto VSIX mediante la **proyecto VSIX** plantilla.  
  
     Se abre Source.Extension.vsixmanifest en **Diseñador de manifiestos**.  
  
3.  En el **activos** ficha, elija la **New** botón.  
  
     El **Agregar nuevo activo** aparece el cuadro de diálogo.  
  
4.  En el **tipo** lista, elija el tipo de extensión que se va a agregar.  
  
5.  Para agregar un elemento de contenido o de extensiones que se incluye en la solución actual (por ejemplo, una plantilla de elementos o un ensamblado compilado), realice los pasos siguientes:  
  
    1.  En el **origen** elija **un proyecto de la solución actual**.  
  
    2.  En el **proyecto** lista, elija el nombre de la extensión.  
  
    3.  En el **insertar en esta carpeta** cuadro, escriba el nombre de una carpeta en la que se va a incrustar el recurso y, a continuación, elija la **Aceptar** botón.  
  
6.  Para agregar una extensión o un elemento de contenido que no se incluye en la solución actual, realice los pasos siguientes:  
  
    1.  En el **origen** cuadro de lista, elija **archivo en filesystem**.  
  
    2.  En el **ruta de acceso** campo, escriba la ruta de acceso completa para el archivo de extensión compiladas o comprimidos o use la **examinar** botón para buscar el archivo.  
  
    3.  En el **insertar en esta carpeta** cuadro, escriba el nombre de una carpeta en la que se va a incrustar el recurso y, a continuación, elija la **Aceptar** botón.  
  
7.  Si desea que el paquete debe incluir extensiones adicionales, agregarlos de la misma manera.  
  
8.  Compile la solución.  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]genera un archivo .vsix que contenga un archivo de manifiesto de VSIX, un archivo [Content_Types] .xml y de todos los activos de extensión que agregan al proyecto.  
  
## <a name="see-also"></a>Vea también  
 [Referencia de esquema 2.0 de extensión VSIX](../extensibility/vsix-extension-schema-2-0-reference.md)   
 [Buscar y usar extensiones de Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)