---
title: "C&#243;mo: Exportar configuraci&#243;n mediante ensamblados de interoperabilidad | Microsoft Docs"
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
  - "configuración del IDE, exportar mediante ensamblados de interoperabilidad"
  - "configuración de usuario [SDK de Visual Studio], exportar mediante ensamblados de interoperabilidad"
  - "IDE, exportar configuración mediante ensamblados de interoperabilidad"
ms.assetid: d470d4f9-3006-40c3-99db-21abcd5003b8
caps.latest.revision: 23
caps.handback.revision: 23
manager: "douge"
---
# C&#243;mo: Exportar configuraci&#243;n mediante ensamblados de interoperabilidad
Un VSPackage puede exportar la configuración de un entorno de desarrollo integrado \(IDE\) [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. El IDE usa la implementación de un VSPackage de la interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings>. Si el paquete también proporciona la interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettingsQuery>, la interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettingsQuery> se usa para determinar cómo se puede guardar configuración de VSPackage.  
  
> [!NOTE]
>  Managed Package Framework \(MPF\) proporciona un conjunto de clases administradas para facilitar la creación de extensiones de Visual Studio. Para realizar esta tarea con MPF, vea [Exportación de configuración](../misc/exporting-settings.md).  
  
### Para implementar la configuración de la exportación en un paquete de VS  
  
1.  Implemente la compatibilidad básica para el mecanismo de configuración [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
    -   Registre el paquete de VS como compatible con el mecanismo de configuración mediante la definición de uno o varios puntos de configuración personalizada.  
  
         Para obtener más información, consulta [Compatibilidad con la configuración de usuario](../extensibility/internals/support-for-user-settings.md).  
  
    -   Declare que implementa VSPackage implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings>. Si lo desea, también VSPackage también puede implementar la interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettingsQuery>. Por ejemplo:  
  
        ```  
        public class MyPackage : IVsPackage, IVsUserSettings, IVsUserSettingsQuery  
        ```  
  
    -   Asegúrese de que la implementación que hace el paquete de VS del método <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> proporciona una interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings> cuando se llama con `IID_IVsUserSettings`.  
  
         Opcionalmente, `QueryInterface` puede proporcionar una interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettingsQuery> cuando se llama con la interfaz `IID_IVsUserSettingsQuery`.  
  
        ```  
        STDMETHODIMP MyPackage::QueryInterface(THIS_ REFIID riid, LPVOID FAR* ppvObj) { if (ppvObj == NULL) return E_POINTER; *ppvObj = NULL; if (riid == IID_IUnknown) *ppvObj = (LPVOID)(IUnknown *)(IClassFactory*)this; else if (riid == IID_IClassFactory) *ppvObj = (LPVOID)(IClassFactory *)this; else if (riid == IID_IVsPackage) *ppvObj = (LPVOID)(IVsPackage *)this; else if (riid == IID_IVsPersistSolutionOpts) *ppvObj = (LPVOID)(IVsPersistSolutionOpts *)this; else if (riid == IID_IVsPersistSolutionProps) *ppvObj = (LPVOID)(IVsPersistSolutionProps *)this; else if (riid == IID_IVsComponentSelectorProvider) *ppvObj = (LPVOID)(IVsComponentSelectorProvider *)this; else if (riid == IID_IVsUserSettings) *ppvObj = (LPVOID)(IVsUserSettings *)this; else if (riid == IID_IVsUserSettingsQuery) *ppvObj = (LPVOID)(IVsUserSettingsQuery *)this; if (*ppvObj) { AddRef(); return NOERROR; } return E_NOINTERFACE; }  
        ```  
  
2.  Opcionalmente, alerte al IDE de la necesidad de exportar una configuración determinada.  
  
     VSPackage puede elegir guardar condicionalmente una configuración que define el estado de punto de configuración personalizado. Por ejemplo, guarde sólo si el usuario indica de forma explícita que se guarde una configuración.  
  
     En este caso, la interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettingsQuery> debe implementarse.  
  
     Si VSPackage no implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettingsQuery>, toda su información de estado se guarda durante la exportación de una configuración.  
  
     VSPackage puede admitir más de un punto de configuración personalizada \(categoría de configuración\). Las implementaciones del método <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettingsQuery.NeedExport%2A> deben comprobar el GUID del punto de configuración personalizado proporcionado o el argumento de categoría de configuración para determinar si se debe guardar un grupo de configuración determinado.  
  
     En el ejemplo siguiente, el VSPackage solicita siempre que se guarde su estado de barra de comandos, pero solo solicita que se guarde su estado de vinculación de clave si se establece una marca.  
  
3.  Escriba los datos de configuración al archivo de configuración.  
  
     Para admitir la configuración de exportación, VSPackage debe implementar siempre el método <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A>.  
  
     La implementación debe controlar los argumentos pasados por el IDE, el GUID de dicha categoría de punto de configuración personalizado y una interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter>.  
  
    1.  VSPackage puede admitir más de un punto de configuración personalizada \(categoría de configuración\). En el ejemplo siguiente, el método <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A> llama a una implementación diferente para mantener el estado de la barra de comandos en lugar de mantener el estado de vinculación de clave.  
  
    2.  VSPackage debe usar la interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter> suministrada para guardar datos en el archivo de configuración.  
  
         `interface IVsSettingsWriter : IUnknown`  
  
         `{`  
  
         `HRESULT WriteSettingString( LPCOLESTR pszSettingName, LPCOLESTR pszSettingValue);`  
  
         `HRESULT WriteSettingLong( LPCOLESTR pszSettingName, long lSettingValue);`  
  
         `HRESULT WriteSettingBoolean( LPCOLESTR pszSettingName, BOOL fSettingValue);`  
  
         `HRESULT WriteSettingBytes( LPCOLESTR pszSettingName, BYTE *pSettingValue, long lDataLength);`  
  
         `HRESULT WriteSettingAttribute( LPCOLESTR pszSettingName, LPCOLESTR pszAttributeName, LPCOLESTR pszSettingValue);`  
  
         `HRESULT WriteSettingXml( IUnknown *pIXMLDOMNode);`  
  
         `HRESULT WriteSettingXmlFromString( LPCOLESTR szXML);`  
  
         `HRESULT ReportError( LPCOLESTR pszError, VSSETTINGSERRORTYPES dwErrorType);`  
  
         `};`  
  
         El valor del argumento `pszSettingName` proporcionado a una interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter> debe identificar de manera exclusiva cada elemento de datos guardado en una categoría de configuración.  
  
        > [!NOTE]
        >  Los nombres deben ser únicos en un punto de configuración personalizado porque el IDE usa su GUID y el valor de `pszSettingName` para identificar cada configuración guardada. Si se invoca más de un método <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter> con el mismo valor de `pszSettingName`, el valor original se sobrescribirá en el archivo de configuración.  
  
         El archivo de configuración admite el acceso aleatorio. Por consiguiente, el orden de lectura y escritura de las operaciones de configuración no es importante.  
  
         Esto se ilustra en las implementaciones de exportación e importación del estado de la barra de comandos \(`ExportSettings_CommandBa`r y `ImportSettings_CommandBar`\) en el ejemplo siguiente.  
  
         Si la implementación puede asignar datos a uno de los cuatro formatos admitidos, no existe ninguna restricción sobre la cantidad o sobre el tipo de los datos que se pueden escribir.  
  
        > [!NOTE]
        >  Además de los datos explícitamente escritos y transparentes para la implementación <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A> la API de configuración también guarda la información de versión de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. La configuración guardada se puede comparar con la versión del IDE que generó la configuración durante la importación de configuración.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra cómo importar y exportar datos de configuración.  
  
```  
// -------------------------------------------------------------------------- //    IVsUserSettings methods used for configuration export. //    Delegate to the right shell object based on the category GUID. // -------------------------------------------------------------------------- static const WCHAR c_szFirstSettingName[] = L"FirstSettingName"; static const WCHAR c_szRandomTrashBytes[] = L"RandomTrashBytes"; static const WCHAR c_szRandomTrashLength[] = L"RandomTrashLength"; static const WCHAR c_szBreakPointWindow[] = L"Breakpoints Window"; // Export Settings. STDMETHOD(NeedExport)(WCHAR* pszCategoryGUID, BOOL *pfNeedExport) { if (!pfNeedExport) return E_INVALIDARG; CLSID clsidCategory; HRESULT hr= S_OK; hr = CLSIDFromString(pszCategoryGUID, &clsidCategory); IfFailGo(hr); if (GUID_Profiles_CommandBars == clsidCategory) { *pfNeedExport = TRUE; //Always export Command Bar Configuration }else if (GUID_Profiles_KeyBindings == clsidCategory) { *pfNeedExport = FALSE; //By Default don't export key bindings if (m_fMake_Permanent) *pfNeedExport = TRUE; //Export if user wants current configuration saved. }else{ hr = E_UNEXPECTED; } Error: return hr; } STDMETHOD(ExportSettings)(WCHAR *pszCategoryGUID, IVsSettingsWriter *pSettings) { CLSID clsidCategory; HRESULT hr; hr = CLSIDFromString(pszCategoryGUID, &clsidCategory); IfFailGo(hr); // Delegate to the right internal implementation based on // the requested category. if (GUID_Profiles_CommandBars == clsidCategory) { hr = ExportSettings_CommandBars(pSettings); }else if (GUID_Profiles_KeyBindings == clsidCategory) { hr = ExportSettings_KeyBindings(pSettings); }else{ hr = E_UNEXPECTED; } Error: return hr; }; HRESULT ExportSettings_CommandBars(IVsSettingsWriter *pSettings) { if (!pSettings) return E_INVALIDARG; hr = pSettings->WriteSettingString(c_szFirstSettingName, L"Value1"); IfFailGo(hr); int cRandomTrash = 12345; BYTE *pRandomTrash = (BYTE *)VSAlloc(cRandomTrash); if (pRandomTrash){ hr = pSettings->WriteSettingBytes(c_szRandomTrashBytes, pRandomTrash, cRandomTrash); IfFailGo(hr); hr = pSettings->WriteSettingLong(c_szRandomTrashLength, cRandomTrash); IfFailGo(hr); } Error: return hr; }; HRESULT ExportSettings_KeyBindings(IVsSettingsWriter *pSettings) { if (!pSettings) return E_INVALIDARG; hr = pSettings->WriteSettingString(c_szBreakPointWindow, L"Ctrl + Alt + B"); IfFailGo(hr); Error: return hr; }; STDMETHOD(ImportSettings)(WCHAR *pszCategoryGUID, IVsSettingsReader *pSettings, UserSettingsFlags flags, BOOL *pfRestartRequired) { CLSID clsidCategory; HRESULT hr; hr = CLSIDFromString(pszCategoryGUID, &clsidCategory); IfFailGo(hr); // Delegate to the right internal implementation based on // the requested category. if (GUID_Profiles_CommandBars == clsidCategory) { hr = ImportSettings_CommandBars(, pSettings, flags, pfRestartRequired); } else if (GUID_Profiles_KeyBindings == clsidCategory) { hr = ImportSettings_KeyBindings( pSettings, flags, pfRestartRequired); } else { hr = E_UNEXPECTED; } Error: return hr; }; // Import Settings. HRESULT ImportSettings_CommandBars(IVsSettingsReader *pSettings, UserSettingsFlags flags, BOOL *pfRestartRequired) { if (!pSettings) return E_INVALIDARG; if (pfRestartRequired) { *pfRestartRequired = FALSE; //Nobody should require a restart!! } CComBSTR bstrFirstSettingName; long lTrashLength = 0; BYTE *pTrashBytes = NULL; // Determines whether to treat import as an additive operation, or a reset all settings operation. BOOL fResetCompletely = FALSE; if (flags & USF_ResetOnImport) fResetCompletely = TRUE; hr = pSettings->ReadSettingString(c_szFirstSettingName, &bstrFirstSettingName); IfFailGo(hr); hr = pSettings->ReadSettingLong(c_szRandomTrashLength, &lTrashLength); IfFailGo(hr); if (lTrashLength > 0) { pTrashBytes = (BYTE*)VSAlloc(lTrashLength); IfNullMemGo(pTrashBytes); long lDataRead = 0; hr = pSettings->ReadSettingBytes(c_szRandomTrashLength, pTrashBytes, &lDataRead, lTrashLength); IfFailGo(hr); if (lDataRead != lTrashLength) { hr = E_UNEXPECTED; goto Error; } } // Note: before returning, these settings should immediately //             be applied to your personal settings store, //             whether in the registry or the file system. // This write-through cache methodology is essential to to work //             in multi-instance IDE scenarios. hr = UpdateState_CommandBar(bstrFirstSettingName,lTrashLength,pTrashBytes,lDataRead); Error: return hr; }; HRESULT ImportSettings_KeyBindings(IVsSettingsReader *pSettings, UserSettingsFlags flags, BOOL *pfRestartRequired) { if (!pSettings) return E_INVALIDARG; if (pfRestartRequired) { *pfRestartRequired = FALSE; //Nobody should require a restart!! } CComBSTR bstrBreakPointWindow; // Determines whether import can be treated as an additive // operation, or a reset all settings operation. BOOL fResetCompletely = FALSE; if (flags & USF_ResetOnImport) fResetCompletely = TRUE; hr = pSettings->ReadSettingString(c_szBreakPointWindow, &bstrBreakPointWindow); IfFailGo(hr); // Note: Before returning, these settings should immediately //             be applied to your personal settings //             store, whether in the registry or the file system. // This write-through cache methodology is essential to allow us //             to work in multi-instance IDE scenarios. hr = UpdateState_KeyBindings(bstrBreakPointWindow); Error: return hr; }  
```  
  
## Vea también  
 [Compatibilidad con la configuración de usuario](../extensibility/internals/support-for-user-settings.md)   
 [Opciones y configuración de usuario de extensión](../extensibility/extending-user-settings-and-options.md)   
 [Personalizar la configuración de desarrollo en Visual Studio](http://msdn.microsoft.com/es-es/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Cómo: Usar ensamblados de interoperabilidad para importar la configuración](../misc/how-to-use-interop-assemblies-to-import-settings.md)