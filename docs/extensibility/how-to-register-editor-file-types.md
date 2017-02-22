---
title: "C&#243;mo: registrar tipos de archivo del Editor | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editores [Visual Studio SDK] heredados - registrar tipos de archivo"
ms.assetid: 54846779-8290-48de-90ab-81011559d9a5
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# C&#243;mo: registrar tipos de archivo del Editor
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La manera más fácil de registrar tipos de archivo del editor está utilizando los atributos del registro proporcionados como parte de las clases administradas [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] \(MPF\) de paquete.  Si está implementando el paquete en código [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)], también puede escribir un script de registro que registre el editor y extensiones asociado.  
  
## Registro mediante clases de MPF  
  
#### Para registrar los tipos de archivo del editor mediante clases de MPF  
  
1.  Proporciona la clase de <xref:Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute> con los parámetros adecuados para el editor en la clase de paquete VSPackage.  
  
    ```  
    [Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute(typeof(EditorFactory), ".Sample", 32,   
         ProjectGuid = "{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3}",   
         TemplateDir = "..\\..\\Templates",   
         NameResourceID = 106)]  
    ```  
  
     donde “. El ejemplo” es la extensión que se registra para este editor, y “32 " es el nivel de prioridad.  
  
     `projectGuid` es un GUID para los tipos de archivos varios, definido en <xref:Microsoft.VisualStudio.VSConstants.CLSID_MiscellaneousFilesProject>.  Proporciona el tipo de archivo diferente, de modo que el archivo resultante no vaya a formar parte del proceso de compilación.  
  
     `TemplateDir` representa la carpeta que contiene los archivos de plantilla que se incluyen con el ejemplo básico administrado del editor.  
  
     `NameResourceID` se define en el archivo de Resources.h de proyectos de BasicEditorUI, e identifica el editor como “mi editor”.  
  
2.  Reemplace el método <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>.  
  
     En la implementación del método de <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> , llame al método de <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> y pase la instancia del generador del editor como se muestra a continuación.  
  
    ```  
    protected override void Initialize()  
    {  
        Trace.WriteLine (string.Format(CultureInfo.CurrentCulture,   
        "Entering Initialize() of: {0}", this.ToString()));  
        base.Initialize();  
           //Create Editor Factory  
        editorFactory = new EditorFactory(this);  
        base.RegisterEditorFactory(editorFactory);  
    }  
    ```  
  
     Este paso registra el generador del editor y extensiones de archivo del editor.  
  
3.  Elimine los generadores del editor.  
  
     Generadores de editor son automáticamente no registradas cuando se elimina el paquete VSPackage.  Si el objeto de generador de editor implementa la interfaz de <xref:System.IDisposable> , se llama a su método de `Dispose` después de que el generador se haya no registrada con [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## Registro Mediante un script de registro  
 Registrar generadores y tipos de archivo del editor de código [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] se hace utilizando un script de registro escribir en el registro de las ventanas, como se muestra en la siguiente.  
  
#### Para registrar los tipos de archivo del editor mediante un script de registro  
  
1.  En el script de registro, defina el generador del editor y la cadena GUID del generador del editor como se muestra en la sección de `GUID_BscEditorFactory` del siguiente script de registro.  Asimismo, defina la extensión y la prioridad de la extensión del editor:  
  
    ```  
  
                NoRemove Editors     {         %GUID_BscEditorFactory% = s 'RTF Editor'         {             val Package = s '%CLSID_Package%'             val DisplayName = s 'An RTF Editor'             val ExcludeDefTextEditor = d 1             val AcceptBinaryFiles = d 0  
  
            LogicalViews  
            {  
                val %LOGVIEWID_TextView% = s ''  
            }  
  
            OpenWithEntries  
            {  
            }  
  
            Extensions             {                 val rtf = d 50             }  
        }  
    }  
    ```  
  
     La extensión de archivo del editor en este ejemplo se identifica como “.rtf” y su prioridad es “50 ".  Las cadenas GUID se definen en el archivo Resource.h del proyecto de ejemplo de BscEdit.  
  
2.  Registre el paquete VSPackage.  
  
3.  Registre el generador del editor.  
  
     El generador del editor se registra en la implementación de <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> .  
  
    ```  
    // create editor factory.  
    if (m_srpEdFact == NULL)   
    {  
        CComObject<CBscEditorFactory> *pEdFact = new CComObject<CBscEditorFactory>;  
        if (NULL == pEdFact)  
          return E_OUTOFMEMORY;  
  
        if (!pEdFact->FInit(this))  
          return E_UNEXPECTED;  
  
        m_srpEdFact = (IVsEditorFactory *) pEdFact;    // Note: assignment to a smart pointer does an AddRef()  
    }  
    // Query service for IVsRegisterEditors, register the editor factory  
    CComPtr<IVsRegisterEditors> srpRegEd;  
    if ((SUCCEEDED(m_srpPkgSiteSP->QueryService(SID_SVsRegisterEditors, IID_IVsRegisterEditors,(void **)&srpRegEd ))) && (srpRegEd != NULL))  
      {  
        ATLTRACE(TEXT(">> CVsPackage, registering editor factory.\n"));  
          if (FAILED(srpRegEd->RegisterEditor(GUID_BscEditorFactory,  
                      m_srpEdFact, &m_dwEditorCookie)))   
          {  
             ATLTRACE(TEXT(">> CVsPackage, RegisterEditor() failed.\n"));  
            return E_FAIL;  
          }  
      }  
        return S_OK;  
    }  
    ```  
  
     Las cadenas GUID se definen en el archivo Resource.h de proyectos de BscEdit.