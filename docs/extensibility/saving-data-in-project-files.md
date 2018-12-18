---
title: Guardar datos en archivos de proyecto | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- data [Visual Studio], saving in project files
- project files
- project files, saving data
ms.assetid: a3d4b15b-a91e-41ba-b235-e62632d11bc5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: adc7d06b8479da4aef7042fd64702cff5ca3be60
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49900662"
---
# <a name="save-data-in-project-files"></a>Guardar datos en archivos de proyecto
Un subtipo de proyecto puede guardar y recuperar datos específicos del subtipo en el archivo de proyecto. Managed Package Framework (MPF) proporciona dos interfaces para realizar esta tarea:  
  
- El <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> interfaz permite a los valores de propiedad de acceso desde el **MSBuild** sección del archivo del proyecto. Los métodos proporcionados por <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> pueden llamarse cualquier usuario siempre que el usuario debe cargar o guardar datos relacionados de compilación.  
  
- El <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> se usa para conservar los datos relacionados de no compilación en XML de forma libre. Los métodos proporcionados por <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> llama [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] cada vez que [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] necesita conservar los datos relacionados de no compilación en el archivo de proyecto.  
  
  Para obtener más información sobre cómo conservar compilación y los datos relacionados de no compilación, véase [conservar los datos en el archivo de proyecto de MSBuild](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md).  
  
## <a name="save-and-retrieve-build-related-data"></a>Guardar y recuperar datos relacionados de la compilación  
  
### <a name="to-save-a-build-related-data-in-the-project-file"></a>Para guardar una compilación relacionados con datos en el archivo de proyecto  
  
-   Llame a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> método para guardar una ruta de acceso completa del archivo del proyecto.  
  
    ```  
    private SpecializedProject project;  
    IVsBuildPropertyStorage projectStorage = (IVsBuildPropertyStorage)project;  
    string newFullPath = GetNewFullPath();  
    // Set a full path of the project file.  
    ErrorHandler.ThrowOnFailure(projectStorage.SetPropertyValue(  
        "MSBuildProjectDirectory",  
        String.Empty,  
        (uint)_PersistStorageType.PST_PROJECT_FILE, newFullPath));  
    ```  
  
### <a name="to-retrieve-build-related-data-from-the-project-file"></a>Para recuperar las compilación relacionados con datos del archivo de proyecto  
  
-   Llame a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.GetPropertyValue%2A> método para recuperar una ruta de acceso completa del archivo del proyecto.  
  
    ```  
    private SpecializedProject project;  
    IVsBuildPropertyStorage projectStorage = (IVsBuildPropertyStorage)project;  
    string fullPath;  
    // Get a full path of the project file.  
    ErrorHandler.ThrowOnFailure(projectStorage.GetPropertyValue(  
        "MSBuildProjectDirectory",  
        String.Empty,  
        (uint)_PersistStorageType.PST_PROJECT_FILE, out fullPath));  
    ```  
  
## <a name="save-and-retrieve-non-build-related-data"></a>Guardar y recuperar datos relacionados de no compilación  
  
### <a name="to-save-non-build-related-data-in-the-project-file"></a>Para guardar sin compilación relacionados con datos en el archivo de proyecto  
  
1.  Implemente el <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.IsFragmentDirty%2A> método para determinar si un fragmento XML ha cambiado desde la última guardó en el archivo actual.  
  
    ```  
    public int IsFragmentDirty(uint storage, out int pfDirty)  
    {  
        pfDirty = 0;  
        switch (storage)  
        {  
            case (uint)_PersistStorageType.PST_PROJECT_FILE:  
            {  
                if (isDirty)  
                    pfDirty |= 1;  
                break;  
            }  
            case (uint)_PersistStorageType.PST_USER_FILE:  
            {  
                // We do not store anything in the user file.  
                break;  
            }  
        }  
  
        // Forward the call to inner flavor(s)   
        if (pfDirty == 0 && innerCfg != null && this.innerCfg is IPersistXMLFragment)  
            return ((IPersistXMLFragment)this.innerCfg).IsFragmentDirty(storage, out pfDirty);  
  
        return VSConstants.S_OK;  
  
    }  
    ```  
  
2.  Implemente el <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A> método para guardar los datos XML en el archivo de proyecto.  
  
    ```  
    public int Save(ref Guid guidFlavor, uint storage, out string pbstrXMLFragment, int fClearDirty)  
    {  
        pbstrXMLFragment = null;  
  
        if (IsMyFlavorGuid(ref guidFlavor))  
        {  
            switch (storage)  
            {  
                case (uint)_PersistStorageType.PST_PROJECT_FILE:  
                {  
                    // Create XML for our data.  
                    XmlDocument doc = new XmlDocument();  
                    XmlNode root = doc.CreateElement(this.GetType().Name);  
  
                    XmlNode node = doc.CreateElement(targetsTag);  
                    node.AppendChild(doc.CreateTextNode(this.TargetsToExecute));  
                    root.AppendChild(node);  
  
                    node = doc.CreateElement(updateTargetsTag);  
                    node.AppendChild(doc.CreateTextNode(this.UpdateTargetList.ToString()));  
                    root.AppendChild(node);  
  
                    doc.AppendChild(root);  
                    // Get XML fragment representing our data  
                    pbstrXMLFragment = doc.InnerXml;  
  
                    if (fClearDirty != 0)  
                        isDirty = false;  
                    break;  
                }  
                case (uint)_PersistStorageType.PST_USER_FILE:  
                {  
                    // We do not store anything in the user file.  
                    break;  
                }  
            }  
        }  
  
        // Forward the call to inner flavor(s)  
        if (this.innerCfg != null && this.innerCfg is IPersistXMLFragment)  
            return ((IPersistXMLFragment)this.innerCfg).Save(ref guidFlavor, storage, out pbstrXMLFragment, fClearDirty);  
  
        return VSConstants.S_OK;  
    }  
    ```  
  
### <a name="to-retrieve-non-build-related-data-in-the-project-file"></a>Para recuperar datos relacionados de no compilación en el archivo de proyecto  
  
1.  Implemente el <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.InitNew%2A> método para inicializar las propiedades de extensión de proyecto y otros datos independientes de la compilación. Se llama a este método si no hay ningún dato de configuración XML está presente en el archivo de proyecto.  
  
    ```  
    public int InitNew(ref Guid guidFlavor, uint storage)  
    {  
        //Return,if it is our guid.  
        if (IsMyFlavorGuid(ref guidFlavor))  
            return VSConstants.S_OK;  
  
        //Forward the call to inner flavor(s).  
        if (this.innerCfg != null && this.innerCfg is IPersistXMLFragment)  
            return ((IPersistXMLFragment)this.innerCfg).InitNew(ref guidFlavor, storage);  
  
        return VSConstants.S_OK;  
    ```  
  
2.  Implemente el <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A> para cargar los datos XML desde el archivo de proyecto.  
  
    ```  
    public int Load(ref Guid guidFlavor, uint storage, string pszXMLFragment)  
    {  
        if (IsMyFlavorGuid(ref guidFlavor))  
        {  
            switch (storage)  
            {  
                case (uint)_PersistStorageType.PST_PROJECT_FILE:  
                {  
                    // Load our data from the XML fragment.  
                    XmlDocument doc = new XmlDocument();  
                    XmlNode node = doc.CreateElement(this.GetType().Name);  
                    node.InnerXml = pszXMLFragment;  
                    if (node == null  
                        || node.FirstChild == null  
                        || node.FirstChild.ChildNodes.Count == 0  
                        || node.FirstChild.ChildNodes[0].Name != targetsTag)  
                        break;  
                    this.TargetsToExecute = node.FirstChild.ChildNodes[0].InnerText;  
  
                    if (node.FirstChild.ChildNodes.Count <= 1  
                        || node.FirstChild.ChildNodes[1].Name != updateTargetsTag)  
                        break;  
                    this.UpdateTargetList = bool.Parse(node.FirstChild.ChildNodes[1].InnerText);  
                    break;  
                }  
                case (uint)_PersistStorageType.PST_USER_FILE:  
                {  
                    // We do not store anything in the user file.  
                    break;  
                }  
            }  
        }  
  
        // Forward the call to inner flavor(s)  
        if (this.innerCfg != null && this.innerCfg is IPersistXMLFragment)  
            return ((IPersistXMLFragment)this.innerCfg).Load(ref guidFlavor, storage, pszXMLFragment);  
  
        return VSConstants.S_OK;  
    }  
    ```  
  
> [!NOTE]
>  Todos los ejemplos de código proporcionados en este tema forman parte de un ejemplo más extenso en [muestras de VSSDK](http://aka.ms/vs2015sdksamples).  
  
## <a name="see-also"></a>Vea también  
 [Conservar los datos en el archivo de proyecto de MSBuild](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)