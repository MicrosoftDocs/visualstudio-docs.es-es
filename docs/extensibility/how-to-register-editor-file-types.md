---
title: 'Cómo: registrar tipos de archivo del Editor | Documentos de Microsoft'
ms.date: 03/22/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - register file types
ms.assetid: 54846779-8290-48de-90ab-81011559d9a5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4ac67139de317c15d4e85be43f7dace132373257
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31129175"
---
# <a name="how-to-register-editor-file-types"></a>Cómo: registrar tipos de archivo del Editor
La manera más fácil para registrar tipos de archivo del editor es mediante el uso de los atributos de registro que se proporciona como parte de la [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] administrado clases package framework (MPF). Si va a implementar el paquete en el modo nativo [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)], también puede escribir un script de registro que registra el editor y las extensiones asociadas.

## <a name="registration-using-mpf-classes"></a>Registro con las clases MPF

#### <a name="to-register-editor-file-types-using-mpf-classes"></a>Para registrar tipos de archivo del editor mediante clases MPF

1.  Proporcionar la <xref:Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute> clase con los parámetros adecuados para el editor de la clase del paquete de VS.

    ```
    [Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute(typeof(EditorFactory), ".Sample", 32,
         ProjectGuid = "{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3}",
         TemplateDir = "..\\..\\Templates",
         NameResourceID = 106)]
    ```

     Donde ". Ejemplo"es la extensión que está registrada para este editor, y"32"es su nivel de prioridad.

     El `projectGuid` es el GUID para los tipos de archivos varios, definidos en <xref:Microsoft.VisualStudio.VSConstants.CLSID.MiscellaneousFilesProject_guid>. Se proporciona el tipo de archivos varios, para que el archivo resultante no se va a formar parte del proceso de compilación.

     `TemplateDir` representa la carpeta que contiene los archivos de plantilla que se incluyen en el ejemplo de editor básico administrado.

     `NameResourceID` se define en el archivo Resources.h del proyecto BasicEditorUI e identifica el editor como "Mi Editor".

2.  Invalide el método <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>.

     En la implementación de la <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> método, llame a la <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> método y pase la instancia de la fábrica de editor como se muestra a continuación.

    ```csharp
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

3.  Anular el registro de los generadores de editores.

     Generadores de editores se elimina automáticamente cuando se elimina el VSPackage. Si el objeto de generador del editor implementa la <xref:System.IDisposable> interfaz, su `Dispose` método se llama después de que el generador se ha anulado el registro con [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

## <a name="registration-using-a-registry-script"></a>Registrar mediante una secuencia de comandos del registro
 Registrar generadores de editores y tipos de archivo en el modo nativo [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] se realiza mediante un script de registro para escribir en el registro de windows, como se muestra en la siguiente.

### <a name="to-register-editor-file-types-using-a-registry-script"></a>Para registrar tipos de archivo del editor mediante un script de registro

1.  En el script del registro, defina el generador del editor y el generador de editores de cadena GUID como se muestra en la `GUID_BscEditorFactory` sección del siguiente script de registro. Además, defina la extensión y la prioridad de la extensión del editor:

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

     La extensión de archivo del editor en este ejemplo se identifica como ".rtf" y su prioridad es "50". Las cadenas del GUID se definen en el archivo Resource.h del proyecto de ejemplo BscEdit.

2.  Registre el VSPackage.

3.  Registrar el generador de editores.

     El generador del editor está registrado en el <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> implementación.

    ```cpp
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