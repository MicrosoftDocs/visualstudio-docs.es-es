---
title: Suministro de soporte de deshacer a los diseñadores Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK], undo support
ms.assetid: 43eb1f14-b129-404a-8806-5bf9b099b67b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0580f974c362a71c3e400946f2ad34f565ad1232
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699674"
---
# <a name="supply-undo-support-to-designers"></a>Soporte de deshacer de suministros a los diseñadores

Los diseñadores, al igual que los editores, normalmente necesitan admitir operaciones de deshacer para que los usuarios puedan revertir sus cambios recientes al modificar un elemento de código.

La mayoría de los diseñadores implementados en Visual Studio tienen compatibilidad con "deshacer" proporcionada automáticamente por el entorno.

Implementaciones de diseñador que necesitan proporcionar compatibilidad con la característica de deshacer:

- Proporcionar administración de deshacer mediante la implementación de la clase base abstracta<xref:System.ComponentModel.Design.UndoEngine>

- Suelen dar persistencia y <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> <xref:System.ComponentModel.Design.IComponentChangeService> compatibilidad con CodeDOM implementando las clases y.

Para obtener más información sobre cómo escribir diseñadores con .NET Framework, vea Extender compatibilidad en [tiempo de diseño](/previous-versions/37899azc(v=vs.140)).

Proporciona [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] una infraestructura de deshacer predeterminada:

- Proporcionar implementaciones de administración <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> de deshacer a través de las clases y.

- Proporcionar persistencia y compatibilidad con <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> CodeDOM a través de las implementaciones y <xref:System.ComponentModel.Design.IComponentChangeService> los valores predeterminados.

## <a name="obtain-undo-support-automatically"></a>Obtener soporte de deshacer automáticamente

Cualquier diseñador creado en Visual Studio tiene compatibilidad de deshacer automática y completa si, el diseñador:

- Hace uso <xref:System.Windows.Forms.Control> de una clase basada para su interfaz de usuario.

- Emplea el sistema estándar de generación y análisis de código basado en CodeDOM para la generación y persistencia de código.

   Para obtener más información acerca de cómo trabajar con compatibilidad con Visual Studio CodeDOM, vea [Generación y compilación](/dotnet/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation)dinámica de código fuente .

## <a name="when-to-use-explicit-designer-undo-support"></a>Cuándo usar el soporte explícito de deshacer del diseñador
 Los diseñadores deben proporcionar su propia administración de deshacer si utilizan una interfaz gráfica <xref:System.Windows.Forms.Control>de usuario, denominada adaptador de vista, distinta de la proporcionada por .

 Un ejemplo de esto podría ser la creación de un producto con una interfaz de diseño gráfico basada en web en lugar de una interfaz gráfica basada en .NET Framework.

 En estos casos, sería necesario registrar este adaptador <xref:Microsoft.VisualStudio.Shell.Design.ProvideViewAdapterAttribute>de vista con Visual Studio mediante , y proporcionar administración de deshacer explícita.

 Los diseñadores deben proporcionar CodeDOM y compatibilidad con la persistencia si <xref:System.CodeDom> no usan el modelo de generación de código de Visual Studio proporcionado en el espacio de nombres.

## <a name="undo-support-features-of-the-designer"></a>Deshacer características de soporte del diseñador
 El SDK de entorno proporciona implementaciones predeterminadas de las interfaces necesarias para proporcionar compatibilidad de deshacer que pueden usar los diseñadores que no usan <xref:System.Windows.Forms.Control> clases basadas para sus interfaces de usuario o el modelo de persistencia y CodeDOM estándar.

 La <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> clase se deriva de <xref:System.ComponentModel.Design.UndoEngine> la clase .NET Framework mediante una implementación de la <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> clase para administrar las operaciones de deshacer.

 Visual Studio proporciona la siguiente característica para deshacer el diseñador:

- Funcionalidad de deshacer vinculada entre varios diseñadores.

- Las unidades secundarias dentro de <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> un <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>diseñador pueden interactuar con sus padres implementando y en .

El SDK de entorno proporciona CodeDOM y compatibilidad con la persistencia al proporcionar:

- <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService>como una implementación de la<xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>

- A <xref:System.ComponentModel.Design.IComponentChangeService> proporcionado por el host de diseño de Visual Studio.

## <a name="use-the-environment-sdk-features-to-supply-undo-support"></a>Use las características del SDK de entorno para proporcionar compatibilidad con Deshacer

Para obtener compatibilidad de deshacer, un objeto que implementa <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> un diseñador <xref:System.IServiceProvider> debe crear instancias e inicializar una instancia de la clase con una implementación válida. Esta <xref:System.IServiceProvider> clase debe proporcionar los siguientes servicios:

- <xref:System.ComponentModel.Design.IDesignerHost>.

- <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>

   Los diseñadores que usan la <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> serialización [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] de Visual Studio <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>CodeDOM pueden optar por usar proporcionado como su implementación de la .

   En este caso, la <xref:System.IServiceProvider> <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> clase proporcionada al constructor debe <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> devolver este objeto como una implementación de la clase.

- <xref:System.ComponentModel.Design.IComponentChangeService>

   Se garantiza <xref:System.ComponentModel.Design.DesignSurface> que los diseñadores que usan el valor predeterminado <xref:System.ComponentModel.Design.IComponentChangeService> proporcionado por el host de diseño de Visual Studio tengan una implementación predeterminada de la clase.

Los diseñadores que implementan un <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> mecanismo de deshacer basado realiza un seguimiento automático de los cambios si:

- Los cambios de <xref:System.ComponentModel.TypeDescriptor> propiedad se realizan a través del objeto.

- <xref:System.ComponentModel.Design.IComponentChangeService>los eventos se generan manualmente cuando se confirma un cambio que se puede deshacer.

- La modificación en el diseñador <xref:System.ComponentModel.Design.DesignerTransaction>se creó en el contexto de un archivo .

- El diseñador elige crear explícitamente unidades de deshacer mediante la unidad <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> de deshacer estándar <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>proporcionada por una <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> implementación o la <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit>implementación específica de Visual Studio , que deriva y también proporciona una implementación de ambos y .

## <a name="see-also"></a>Vea también

- <xref:System.ComponentModel.Design.UndoEngine>
- <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>
- [Amplíe el soporte en tiempo de diseño](/previous-versions/37899azc(v=vs.140))
