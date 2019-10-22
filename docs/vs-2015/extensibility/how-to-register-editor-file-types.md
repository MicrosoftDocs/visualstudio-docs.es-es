---
title: Procedimiento Registrar tipos de archivo del Editor | Documentos de Microsoft
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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68204117"
---
# <a name="how-to-register-editor-file-types"></a>Procedimiento Registro de tipos de archivo del editor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Es la manera más fácil para registrar los tipos de archivo del editor mediante el uso de los atributos de registro proporcionados como parte de la [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] clases de managed package framework (MPF). Si está implementando el paquete en el modo nativo [!INCLUDE[vcprvc](../includes/vcprvc-md.md)], también puede escribir un script de registro que registra el editor y las extensiones asociadas.  
  
## <a name="registration-using-mpf-classes"></a>Registro de uso de clases MPF  
  
#### <a name="to-register-editor-file-types-using-mpf-classes"></a>Para registrar los tipos de archivo del editor mediante las clases MPF  
  
1. Proporcione el <xref:Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute> clase con los parámetros adecuados para el editor de la clase del paquete VSPackage.  
  
    ```  
    [Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute(typeof(EditorFactory), ".Sample", 32,   
         ProjectGuid = "{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3}",   
         TemplateDir = "..\\..\\Templates",   
         NameResourceID = 106)]  
    ```  
  
     Donde ". Ejemplo de"es la extensión que está registrada para este editor y"32"es su nivel de prioridad.  
  
     El `projectGuid` es el GUID de tipos de archivos varios, definidos en <xref:Microsoft.VisualStudio.VSConstants.CLSID.MiscellaneousFilesProject_guid>. Se proporciona el tipo de archivos varios, para que el archivo resultante no se va a formar parte del proceso de compilación.  
  
     `TemplateDir` representa la carpeta que contiene los archivos de plantilla que se incluyen en el ejemplo administrado editor básico.  
  
     `NameResourceID` se define en el archivo Resources.h del proyecto BasicEditorUI e identifica el editor como "Mi Editor".  
  
2. Invalide el método <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> .  
  
     En la implementación de la <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> método, llame a la <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> método y pase la instancia de su generador de editores como se muestra a continuación.  
  
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
  
3. Anular el registro de los generadores de editores.  
  
     Generadores de editores se elimina automáticamente cuando se desecha el VSPackage. Si el objeto de generador del editor implementa la <xref:System.IDisposable> interfaz, su `Dispose` se llama al método después de que se ha registrado la fábrica con [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="registration-using-a-registry-script"></a>Registro mediante un Script de registro  
 Registrar generadores de editores y tipos de archivo en el modo nativo [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] se realiza mediante un script de registro para escribir en el registro de windows, como se muestra en la siguiente.  
  
#### <a name="to-register-editor-file-types-using-a-registry-script"></a>Para registrar los tipos de archivo del editor mediante un script de registro  
  
1. En el script del registro, definir el generador de editores y la cadena GUID del generador de editores como se muestra en la `GUID_BscEditorFactory` sección del siguiente script de registro. Asimismo, defina la extensión y la prioridad de la extensión del editor:  
  
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
  
     La extensión de archivo del editor en este ejemplo se identifica como "RTF" y su prioridad es "50". Las cadenas del GUID se definen en el archivo Resource.h del proyecto de ejemplo BscEdit.  
  
2. Registre el VSPackage.  
  
3. Registre el generador de editores.  
  
     El generador de editores se registra en el <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> implementación.  
  
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
  
     Las cadenas del GUID se definen en el archivo Resource.h del proyecto BscEdit.
