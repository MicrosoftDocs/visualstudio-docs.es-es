---
title: Activación en contexto | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - in-place view activation
ms.assetid: 7d316945-06e0-4d8e-ba3a-0ef96fc75399
caps.latest.revision: 26
manager: jillfra
ms.openlocfilehash: 192274d087731f68cb7e01c1da20e80cbfef0360
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "64802925"
---
# <a name="in-place-activation"></a>Activación en contexto
Si la vista del editor hospeda ActiveX u otros controles activos, debe implementar la vista del editor como un control ActiveX o como un objeto de datos de documento activo mediante el modelo de activación en contexto.  
  
## <a name="support-for-menus-toolbars-and-commands"></a>Compatibilidad con menús, barras de herramientas y comandos  
 Visual Studio permite que vista del editor use los menús y las barras de herramientas del IDE. Estas extensiones se conocen como *componentes OLE en contexto*. Para obtener más información, vea <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent> y <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager>.  
  
 Si implementa un control ActiveX, puede hospedar otros objetos incrustados. Si implementa un objeto de datos del documento, el marco de ventana restringe la capacidad de usar controles ActiveX.  
  
> [!NOTE]
> Las interfaces <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument> y <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocumentView> permiten una separación de los datos y la vista. Sin embargo, Visual Studio no admite estas características y estas interfaces se usan únicamente para representar el objeto de la vista de documento.  
  
 Los editores que usan el servicio <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> pueden proporcionar integración de menús, barras de herramientas y comandos mediante la llamada a los métodos de la interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> implementada por el servicio <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> . Los editores también pueden ofrecer otras funciones de Visual Studio, como el seguimiento de selección y la administración de deshacer. Para obtener más información, vea [crear editores y diseñadores personalizados](../extensibility/creating-custom-editors-and-designers.md).  
  
## <a name="objects-and-interfaces-used"></a>Objetos e interfaces usados  
 En la siguiente ilustración, se muestran los objetos usados para crear la activación en contexto.  
  
 ![En&#45;colocar el editor de activación](../misc/media/vsinplaceactivationeditor.gif "vsInPlaceActivationEditor")  
Editor de activación en contexto  
  
> [!NOTE]
> De los objetos de este dibujo, solo el objeto `CYourEditorFactory` es necesario para crear un editor estándar. Si está creando un editor personalizado, no es necesario que implemente <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> , ya que el editor tendrá probablemente su propio mecanismo de persistencia privado. Para obtener más información, vea [crear editores y diseñadores personalizados](../extensibility/creating-custom-editors-and-designers.md).  
  
 Todas las interfaces implementadas para crear un editor de activación en contexto se muestran en el objeto `CYourEditorDocument` único, pero esta configuración admite solamente una vista única de los datos del documento. Para obtener más información sobre la compatibilidad con varias vistas de los datos del documento, consulte [Supporting Multiple Document Views](../extensibility/supporting-multiple-document-views.md).  
  
|Interfaz|Tipo de objeto|Usar|  
|---------------|--------------------|---------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent>|Ver|Permite que los objetos de VSPackage en contexto funcionen como componentes totalmente integrados del IDE mediante el servicio <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> . Este servicio integra los menús, las barras de herramientas y los comandos del objeto en el IDE y emite notificaciones de los cambios de estado.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleObject>|Ver|Medios principales por los que un objeto incrustado proporciona características básicas a su contenedor y se comunica con este.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceActiveObject>|Ver|Administra la activación y desactivación de los objetos en contexto, y determina la cantidad del objeto en contexto que debe estar visible.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceObject>|Ver|Proporciona un canal directo de comunicación entre un objeto en contexto, la ventana de marco exterior de la aplicación asociada y la ventana del documento en la aplicación que contiene el objeto incrustado.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument>|Ver|Implementa un objeto ActiveX. Tenga en cuenta que los métodos de <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument> y `T:Microsoft.VisualStudio.OLE.Interop.IOleDocumentView` que separan los datos y la vista del documento no se usan en el IDE.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Ver/datos|Permite que el objeto de datos del documento, el objeto de vista de documento o ambos participen en la gestión de comandos.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>|Ver|Habilita las actualizaciones de la barra de estado.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>|Ver|Permite agregar elementos al cuadro de herramientas.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEvents>|data|Envía una notificación de los cambios realizados en el archivo editado. (Esta interfaz es opcional).|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|data|Se usa para habilitar la característica Guardar como para un tipo de archivo.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|data|Habilita la persistencia del documento. Para los archivos de solo lectura, llame a <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.SetDocDataReadOnly%2A> para proporcionar el icono "bloquear" que indica que los archivos son de solo lectura.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>|data|Determina si los cambios realizados en los datos del documento deben omitirse.|