---
title: 'Cómo: registrar tipos de archivo del editor | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - register file types
ms.assetid: 54846779-8290-48de-90ab-81011559d9a5
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8d22e61d88b5f6e3959a369f6957efbc824384b2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204117"
---
# <a name="how-to-register-editor-file-types"></a>Cómo: Registrar tipos de archivo del editor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La manera más fácil de registrar los tipos de archivo del editor es usar los atributos de registro que se proporcionan como parte de las [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] clases de Managed Package Framework (MPF). Si está implementando el paquete en nativo [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] , también puede escribir un script del registro que registre el editor y las extensiones asociadas.  
  
## <a name="registration-using-mpf-classes"></a>Registro mediante clases MPF  
  
#### <a name="to-register-editor-file-types-using-mpf-classes"></a>Para registrar tipos de archivo del editor mediante clases MPF  
  
1. Proporcione la <xref:Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute> clase con los parámetros adecuados para el editor en la clase del VSPackage.  
  
    ```  
    [Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute(typeof(EditorFactory), ".Sample", 32,   
         ProjectGuid = "{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3}",   
         TemplateDir = "..\\..\\Templates",   
         NameResourceID = 106)]  
    ```  
  
     Where ". Ejemplo "es la extensión registrada para este editor y" 32 "es su nivel de prioridad.  
  
     `projectGuid`Es el GUID para tipos de archivo varios, definidos en <xref:Microsoft.VisualStudio.VSConstants.CLSID.MiscellaneousFilesProject_guid> . Se proporciona el tipo de archivo varios, por lo que el archivo resultante no va a formar parte del proceso de compilación.  
  
     `TemplateDir` representa la carpeta que contiene los archivos de plantilla que se incluyen con el ejemplo del editor básico administrado.  
  
     `NameResourceID` se define en el archivo resources. h del proyecto BasicEditorUI e identifica el editor como "My editor".  
  
2. Invalide el método <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>.  
  
     En la implementación del <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> método, llame al <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> método y pase la instancia del generador de editores tal y como se muestra a continuación.  
  
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
  
     Este paso registra el generador de editores y las extensiones de archivo del editor.  
  
3. Anule el registro de los generadores de editores.  
  
     Los generadores de editores se anulan automáticamente cuando se elimina el VSPackage. Si el objeto de generador de editores implementa la <xref:System.IDisposable> interfaz, `Dispose` se llama a su método una vez que se ha anulado el registro del generador con [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
## <a name="registration-using-a-registry-script"></a>Registro mediante un script del registro  
 El registro de generadores y tipos de archivo en nativo [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] se realiza mediante un script del registro para escribir en el registro de Windows, como se muestra a continuación.  
  
#### <a name="to-register-editor-file-types-using-a-registry-script"></a>Para registrar tipos de archivo del editor mediante un script del registro  
  
1. En el script del registro, defina el generador de editores y la cadena GUID del generador de editores, tal como se muestra en la `GUID_BscEditorFactory` sección del siguiente script del registro. Además, defina la extensión y la prioridad de la extensión del editor:  
  
    ```  
  
          NoRemove Editors     {         %GUID_BscEditorFactory% = s 'RTF Editor'         {             val Package = s '%CLSID_Package%'             val DisplayName = s 'An RTF Editor'             val ExcludeDefTextEditor = d 1             val AcceptBinaryFiles = d 0  
  
            LogicalViews  
            {  
                val %LOGVIEWID_TextView% = s ''  
            }  
  
            OpenWithEntries  
            {  
            }  
  
            Extensions            {                val rtf = d 50            }  
        }  
    }  
    ```  
  
     La extensión de archivo del editor en este ejemplo se identifica como ". rtf" y su prioridad es "50". Las cadenas GUID se definen en el archivo resource. h del proyecto de ejemplo BscEdit.  
  
2. Registre el VSPackage.  
  
3. Registre el generador de editores.  
  
     El generador de editores se registra en la <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> implementación de.  
  
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
  
     Las cadenas GUID se definen en el archivo resource. h del proyecto BscEdit.
