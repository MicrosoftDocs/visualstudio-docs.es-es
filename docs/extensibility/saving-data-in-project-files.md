---
title: Guardar datos en archivos de proyecto | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data [Visual Studio], saving in project files
- project files
- project files, saving data
ms.assetid: a3d4b15b-a91e-41ba-b235-e62632d11bc5
caps.latest.revision: "28"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 42273797b1010afdee3d317e7aa2e6ae4362a7bc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="saving-data-in-project-files"></a>Guardar datos en archivos de proyecto
Un subtipo de proyecto puede guardar y recuperar datos específicos de subtipo en el archivo de proyecto. Managed Package Framework (MPF) proporciona dos interfaces para realizar esta tarea:  
  
-   El <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> interfaz permite a los valores de propiedad de acceso de la **MSBuild** sección del archivo del proyecto. Los métodos proporcionados por <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> puede llamarse mediante cualquier usuario siempre que el usuario sólo necesita cargar o guardar genera datos relacionados.  
  
-   El <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> se utiliza para conservar los datos relacionados de compilación no en XML de forma libre. Los métodos proporcionados por <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> llama a [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] cada vez que [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] necesita conservar datos relacionados de compilación no en el archivo de proyecto.  
  
 Para obtener más información acerca de cómo conservar compilación y los datos relacionados de no compilación, consulte [guardar datos en el archivo de proyecto de MSBuild](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md).  
  
## <a name="saving-and-retrieving-build-related-data"></a>Guardar y recuperar compilación relacionados con datos  
  
#### <a name="to-save-a-build-related-data-in-the-project-file"></a>Para guardar una compilación relacionados con datos en el archivo de proyecto  
  
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
  
#### <a name="to-retrieve-build-related-data-from-the-project-file"></a>Para recuperar la compilación relacionados con datos del archivo de proyecto  
  
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
  
## <a name="saving-and-retrieving-non-build-related-data"></a>Guardar y recuperar no-compilación datos relacionados  
  
#### <a name="to-save-non-build-related-data-in-the-project-file"></a>Para guardar la compilación no relacionadas con datos en el archivo de proyecto  
  
1.  Implemente el <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.IsFragmentDirty%2A> método para determinar si un fragmento XML ha cambiado desde la última guarda en su archivo actual.  
  
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
  
#### <a name="to-retrieve-non-build-related-data-in-the-project-file"></a>Para recuperar datos relacionados de compilación no en el archivo de proyecto  
  
1.  Implemente el <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.InitNew%2A> método para inicializar las propiedades de extensión de proyecto y otros datos independiente de la compilación. Se llama a este método si no hay ningún dato de configuración XML está presente en el archivo de proyecto.  
  
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
  
2.  Implemente el <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A> método para cargar los datos XML desde el archivo de proyecto.  
  
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
 [Conservación de datos en el archivo de proyecto de MSBuild](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)