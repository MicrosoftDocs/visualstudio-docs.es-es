---
title: "C&#243;mo: admitir la funci&#243;n de arrastrar y colocar en el cuadro de herramientas | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "función de arrastrar y colocar, admitir en cuadro de herramientas"
  - "Cuadro de herramientas [SDK de Visual Studio], cliente"
  - "Cuadro de herramientas [SDK de Visual Studio], función de arrastrar y colocar"
ms.assetid: 2f73a03c-1eb1-4b88-9c1b-d63ba0e2ac90
caps.latest.revision: 18
caps.handback.revision: 18
manager: "douge"
---
# C&#243;mo: admitir la funci&#243;n de arrastrar y colocar en el cuadro de herramientas
> [!NOTE]
>  La forma recomendada de agregar controles personalizados al cuadro de herramientas es usar las plantillas del control de cuadro de herramientas que vienen con Visual Studio 10 SDK, que incluye compatibilidad con la función de arrastrar y colocar. Este tema se conserva únicamente para fines de compatibilidad con versiones anteriores y para trabajar con los controles existentes.  
>   
>  Para obtener más información sobre cómo crear controles de cuadro de herramientas mediante plantillas, consulte [Cómo: Crear un control Toolbox que use formularios Windows Forms](../misc/how-to-create-a-toolbox-control-that-uses-windows-forms.md) y [Crear un Control de cuadro de herramientas WPF](../extensibility/creating-a-wpf-toolbox-control.md).  
  
 Los paquetes VSPackage deben implementar la compatibilidad con la función de arrastrar y colocar si van a usar controles de **Cuadro de herramientas** en las vistas de documento como, por ejemplo, editores o diseñadores.  
  
 De forma predeterminada, todos los objetos de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] derivados de <xref:System.Windows.Forms.Control?displayProperty=fullName> proporcionan, automática y transparente, compatibilidad para consumir controles de **Cuadro de herramientas** y, por lo tanto, los procedimientos descritos a continuación no son necesarios. La función básica puede extenderse mediante la creación de un diseñador.  
  
 Para obtener más información, consulte [Información general sobre formularios Windows Forms](../Topic/Windows%20Forms%20Overview.md) y [Extending Design\-Time Support](../Topic/Extending%20Design-Time%20Support.md).  
  
### Para implementar la función básica de arrastrar y colocar  
  
1.  Proporcione compatibilidad con la característica de arrastrar y colocar implementando <xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget> en un objeto de vista. Esto ofrece la vista con la función de arrastrar y colocar de OLE y la serialización del control.  
  
     Para obtener más información sobre cómo implementar la función de arrastrar y colocar, vea [Arrastrar y colocar \(OLE\)](/visual-cpp/mfc/drag-and-drop-ole).  
  
     Los destinos de la colocación pueden ser elementos o controles del Portapapeles que se colocan en un diseñador. Para obtener más información sobre los formatos estándar de Portapapeles admitidos por el **Cuadro de herramientas** de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], vea [Extensión del Cuadro de herramientas](../misc/extending-the-toolbox.md).  
  
2.  Proporcione una implementación básica de la interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser> en una vista de documento.  
  
     Cuando un usuario intenta arrastrar un control de cuadro de herramientas a una vista, el shell de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] consulta el paquete VSPackage de la vista para ver si este implementa la interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>.  
  
    1.  Implemente <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser.IsSupported%2A> para devolver <xref:Microsoft.VisualStudio.VSConstants.S_OK> a aquellos formatos de **cuadro de herramientas** que admite el destino de colocación. En el ejemplo siguiente se comprueba si el objeto de datos tiene un formato de Portapapeles personalizado \(`CF_CUSTOM_FORMAT`\) y si el objeto es un control ActiveX.  
  
        ```cpp#  
        STDMETHODIMP CustTbxUser::IsSupported(IDataObject* pDO) { HRESULT hr; STGMEDIUM stm; if (!pDO) return E_POINTER; // Determine if the data object is in the Custom clip board format // fetc is the dialog editor toolbox item template. FORMATETC fetc = { m_CF_CUSTOM_FORMAT, //Value set with RegisterClipboardFormat NULL, DVASPECT_CONTENT, // DVASCPECT_ICON might be better -1, TYMED_HGLOBAL }; if (FAILED(hr = pDO->GetData(&fetc, &stm))) { // Determine if the object is in the class-id clipboard format ... this // would be the case if the control is an activeX toolbox item. FORMATETC xfetc = { m_CF_CLSID, NULL, DVASPECT_CONTENT, // DVASCPECT_ICON might be better -1, TYMED_HGLOBAL }; if (SUCCEEDED(hr = pDO->GetData(&xfetc,&stm))) { USES_CONVERSION; GUID guid; LPSTR pData = (LPSTR)GlobalLock(stm.hGlobal); if (pData) { // Convert from the string format to a binary GUID. if (CLSIDFromString(A2W(pData), &guid) != S_OK) return E_FAIL; // HTML data objects could have CLSID format ... so any data object could // be returned as a NULL guid ... fail on null guid, obviously they are // not active X controls. if (guid == GUID_NULL) return E_FAIL; } } } return hr; }  
        ```  
  
         El IDE comprueba esta información cuando una ventana de la vista se carga por primera vez y por cada activación de ventana de la vista después de que un usuario restablece el **Cuadro de herramientas** mediante el cuadro de diálogo **Personalizar Cuadro de herramientas** del IDE. Normalmente, en **Cuadro de herramientas** no se muestran elementos no compatibles con **Cuadro de herramientas**.  
  
         Los usuarios pueden establecer una opción para mostrar todas las páginas de cuadro de herramientas en todo momento. En este caso, el entorno no consultará el editor para <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser.IsSupported%2A>.  
  
    2.  Después de que una implementación de <xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget> \(como la descrita anteriormente\) controla de forma correcta un componente colocado, el objeto de vista debe notificar esto al entorno de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] mediante una llamada a <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2.DataUsed%2A>.  
  
     Si lo prefiere, un VSPackage puede extender su compatibilidad con la función de arrastrar y colocar al ampliar su propia implementación de <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>.  
  
3.  Una implementación de <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser> puede admitir la operación de arrastre de elementos de **Cuadro de herramientas** a una ventana por selección en vez de por una acción del mouse. Es decir, se arrastra un elemento cuando un usuario hace doble clic en un elemento de **Cuadro de herramientas** o hace un solo clic y luego presiona ENTRAR. Para hacerlo:  
  
    1.  Implemente el método <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser.ItemPicked%2A>.  
  
         Este método, llamado por el IDE, se selecciona través de un clic o presionando ENTRAR.  
  
         El método debe insertar el elemento de **Cuadro de herramientas** en la ventana de destino.  
  
    2.  Si no quiere admitir la implementación por selección, el método debe devolver <xref:Microsoft.VisualStudio.VSConstants.S_FALSE>.  
  
         En el ejemplo siguiente, la implementación del método <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser.ItemPicked%2A> comprueba si se admite el objeto seleccionado y, si es así, lo deserializa en el código:  
  
        ```cpp#  
        STDMETHODIMP CustTbxUser::ItemPicked(IDataObject* pDataObject) { if (!pDataObject) return E_POINTER; UINT nIDTool; if (IsSupported(pDataObject) == S_OK) { SetToolCursor(); m_pDataObject = pDataObject; nIDTool = DeserializeObject(); // Get the focus back m_pResObject->m_spWndFrame->Show(); return S_OK; } }  
        ```  
  
4.  Siga los pasos a continuación para asegurarse de que el foco correspondiente se mantiene en su aplicación:  
  
    1.  Si la ventana del editor implementa dos paneles diferentes, no dos vistas diferentes, entonces llame al método <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2.UpdateToolboxUI%2A> cuando cambie las activaciones de panel en la ventana del editor. Solo usted puede saber cuándo se producen cambios de activación dentro de su ventana.  
  
    2.  Para activar correctamente la ventana y asegurarse de que el enrutamiento de comandos se actualiza de forma adecuada, debe llamar al método <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> en el componente. Esta acción debe realizarse al establecer el foco en una ventana de componente \(por ejemplo, un editor\), creada o modificada por una operación de arrastrar y colocar asociada al cuadro de herramientas.  
  
 Es posible que un paquete VSPackage tenga que intervenir en una operación de arrastre y modifique el elemento colocado a través de la interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxActiveUserHook>.  
  
 Por ejemplo, en lugar de agregar un nuevo control de **Cuadro de herramientas** explícitamente en el **Cuadro de herramientas**, un VSPackage podría interceptar un **Cuadro de herramientas** estándar en el momento de la colocación y reemplazarlo por una implementación personalizada.  
  
### Para modificar dinámicamente los controles de cuadro de herramientas  
  
1.  Implemente el método <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxActiveUserHook>.  
  
     Siempre que se selecciona o se coloca un elemento de **Cuadro de herramientas**, el **Cuadro de herramientas** consulta el destino de colocación para saber si este admite la interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxActiveUserHook>, y si es así, llama al método <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxActiveUserHook.InterceptDataObject%2A>.  
  
2.  El método <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxActiveUserHook.InterceptDataObject%2A> debe devolver un nuevo objeto <xref:Microsoft.VisualStudio.OLE.Interop.IDataObject> que se usará en lugar del objeto <xref:Microsoft.VisualStudio.OLE.Interop.IDataObject> original.  
  
     Si el destino de colocación no necesita invalidar el objeto de datos, debe devolver su entrada.  
  
 Un paquete VSPackage puede permitir el desplazamiento de los usuarios por el contenido del Portapapeles al presionar CTRL\+MAYÚS\+V.  
  
### Para admitir un anillo del Portapapeles  
  
1.  Implemente un controlador para el comando `CMDIDPasteNextTBXCBItem` mediante:  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> para paquetes VSPackage basados en ensamblados de interoperabilidad.  
  
    -   <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> para paquetes VSPackage basados en Managed Package Framework. la interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxClipboardCycler>.  
  
2.  En el controlador de comandos, implemente el método <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxClipboardCycler.AreDataObjectsAvailable%2A> para determinar si hay algún objeto de Portapapeles para recorrer.  
  
    1.  Si no hay elementos en el Portapapeles del cuadro de herramientas, el entorno comprueba el Portapapeles del sistema para ver si hay elementos en él.  
  
    2.  Si hay elementos en el Portapapeles del sistema, pero no en el Portapapeles del cuadro de herramientas, el anillo del Portapapeles se rellena con elementos del sistema.  
  
    3.  Para seleccionar el próximo elemento de la lista, la implementación llama al método <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxClipboardCycler.GetAndSelectNextDataObject%2A>.  
  
    4.  Para volver al principio del ciclo del Portapapeles, se debe llamar al método <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxClipboardCycler.BeginCycle%2A>.  
  
## Vea también  
 [Extensión del Cuadro de herramientas](../misc/extending-the-toolbox.md)   
 [Cómo: Proporcionar elementos de Cuadro de herramientas personalizados mediante ensamblados de interoperabilidad](../misc/how-to-provide-custom-toolbox-items-by-using-interop-assemblies.md)   
 [Desarrollo avanzado de controles del cuadro de herramientas](../misc/advanced-toolbox-control-development.md)   
 [Registrar características de compatibilidad del Cuadro de herramientas](../misc/registering-toolbox-support-features.md)   
 [Administración del cuadro de herramientas](../misc/managing-the-toolbox.md)