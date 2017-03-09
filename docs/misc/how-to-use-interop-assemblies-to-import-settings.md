---
title: "C&#243;mo: Usar ensamblados de interoperabilidad para importar la configuraci&#243;n | Microsoft Docs"
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
  - "configuración del IDE, importar mediante ensamblados de interoperabilidad"
  - "ID, importar configuración mediante ensamblados de interoperabilidad"
  - "configuración de usuario [SDK de Visual Studio], importar mediante ensamblados de interoperabilidad"
ms.assetid: 8a43dbe2-fdc0-471b-8235-3f489b77db0f
caps.latest.revision: 26
caps.handback.revision: 26
manager: "douge"
---
# C&#243;mo: Usar ensamblados de interoperabilidad para importar la configuraci&#243;n
Un VSPackage puede importar la configuración de un Entorno de desarrollo integrado \(IDE\) [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. El IDE usa la implementación que hace un VSPackage de la interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings> para determinar cómo se debe recuperar la configuración del VSPackage.  
  
> [!NOTE]
>  Managed Package Framework \(MPF\) proporciona un conjunto de clases administradas para facilitar la creación de extensiones de Visual Studio. Para realizar esta tarea con MPF, vea [Importación de la configuración](../misc/importing-settings.md).  
  
### Para implementar la configuración de la importación en un VSPackage  
  
1.  Implemente la compatibilidad básica para el mecanismo de configuración [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
    -   Registre el VSPackage como compatible con el mecanismo de configuración mediante la definición de uno o varios puntos de configuración personalizada.  
  
         Para obtener más información, consulta [Compatibilidad con la configuración de usuario](../extensibility/internals/support-for-user-settings.md).  
  
    -   Declare que el VSPackage implementa la interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings>, por ejemplo:  
  
        ```  
        public class MyPackage : IVsPackage, IVsUserSettings, IVsUserSettingsQuery  
        ```  
  
    -   Asegúrese de que la implementación que hace el VSPackage del método <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> proporciona una interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings> cuando se llama con `IID_IVsUserSettings`. Por ejemplo:  
  
        ```  
        STDMETHODIMP MyPackage::QueryInterface(THIS_ REFIID riid, LPVOID FAR* ppvObj) { if (ppvObj == NULL) return E_POINTER; *ppvObj = NULL; if (riid == IID_IUnknown) *ppvObj = (LPVOID)(IUnknown *)(IClassFactory*)this; else if (riid == IID_IClassFactory) *ppvObj = (LPVOID)(IClassFactory *)this; else if (riid == IID_IVsPackage) *ppvObj = (LPVOID)(IVsPackage *)this; else if (riid == IID_IVsPersistSolutionOpts) *ppvObj = (LPVOID)(IVsPersistSolutionOpts *)this; else if (riid == IID_IVsPersistSolutionProps) *ppvObj = (LPVOID)(IVsPersistSolutionProps *)this; else if (riid == IID_IVsComponentSelectorProvider) *ppvObj = (LPVOID)(IVsComponentSelectorProvider *)this; else if (riid == IID_IVsUserSettings) *ppvObj = (LPVOID)(IVsUserSettings *)this; else if (riid == IID_IVsUserSettingsQuery) *ppvObj = (LPVOID)(IVsUserSettingsQuery *)this; if (*ppvObj) { AddRef(); return NOERROR; } return E_NOINTERFACE; }  
        ```  
  
2.  Recupere la información de configuración.  
  
     Para admitir la recuperación de la información de configuración, un VSPackage debe implementar el método <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A>.  
  
     Para leer datos, la implementación que hace un VSPackage de la interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings> debe usar los dos primeros argumentos pasados por el IDE: el GUID de categoría de ese punto de configuración personalizado y una interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader>.  
  
    1.  La implementación que hace un VSPackage del método <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> debe comprobar el GUID de categoría que se pasa y elegir el mecanismo correcto para el estado de recuperación.  
  
         En el ejemplo siguiente, el método <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> llama a una implementación diferente para recuperar el estado de la barra de comandos en lugar de recuperar el estado de enlace de teclado.  
  
    2.  Un VSPackage debe usar la interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader> suministrada para recuperar datos para el archivo de configuración.  
  
        > [!NOTE]
        >  Si cambia la información de configuración como una función de una versión de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], la implementación que hace un VSPackage del método <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> debe usar el método <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader.ReadFileVersion%2A> antes de leer los datos para comprobar la versión de IDE.  
  
         La interfaz proporciona métodos para leer los distintos tipos de datos del archivo de configuración.  
  
         `interface IVsSettingsReader : IUnknown`  
  
         `{`  
  
         `HRESULT ReadSettingString(WCHAR *pszSettingName, BSTR *pbstrSettingValue);`  
  
         `HRESULT ReadSettingLong(WCHAR *pszSettingName, long *plSettingValue);`  
  
         `HRESULT ReadSettingBoolean(WCHAR *pszSettingName, BOOL *pfSettingValue);`  
  
         `HRESULT ReadSettingAttribute(LPCOLESTR pszSettingName,LPCOLESTR pszAttributeName, BSTR *pbstrSettingValue);  //Internal use only`  
  
         `HRESULT ReadSettingBytes(WCHAR *pszSettingName, BYTE *pSettingValue, long *plDataLength, long lDataMax);`  
  
         `HRESULT ReadVersion(int *pnMajor, int *pnMinor, int *pnBuild);`  
  
         `HRESULT ReportError(WCHAR *pszError);`  
  
         `};`  
  
     El archivo de configuración admite el acceso a datos aleatorio, por lo que el orden de lectura y escritura de las operaciones de configuración no es importante.  
  
     Esto se ilustra en la exportación e importación del estado de la barra de comandos \(`ExportSettings_CommandBa`r y `ImportSettings_CommandBar`\) de la implementación en el ejemplo siguiente.  
  
3.  Valide los datos recuperados.  
  
     La información de configuración se encuentra en archivos XML, que pueden modificarse manualmente.  
  
> [!IMPORTANT]
>  La información de configuración puede dañarse en el disco, puede contener configuración específica de la versión y podría usarse como vehículo para ataques malintencionados. La validez de cada elemento de datos devuelto por el método <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader> debe validarse.  
  
-   Para comprobar la compatibilidad de la versión de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] usado para generar la configuración recuperada, llame al método <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader.ReadFileVersion%2A> para recuperar la versión.  
  
-   Para hacer que el IDE notifique a un usuario que no se valida un elemento de datos importado, un VSPackage llama al método <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader.ReportError%2A>.  
  
1.  Aplique la información de configuración.  
  
    1.  La implementación del método <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> debe respetar el valor del tercer argumento que el IDE le pasa. Los valores admitidos son miembros de la enumeración <xref:Microsoft.VisualStudio.Shell.Interop.__UserSettingsFlags>. Para obtener más información, consulta <xref:Microsoft.VisualStudio.Shell.Interop.__UserSettingsFlags>.  
  
         En el ejemplo siguiente, la implementación para la importación de la configuración de la barra de comandos \(`ImportSettings_Commandbar`\) usa el valor de este argumento para determinar si se debe aplicar la configuración para sobrescribir los valores existentes o para actualizarlos mediante agregación.  
  
    2.  Debe implementar una metodología de caché de escritura simultánea al aplicar la configuración importada.  
  
         La información de estado en el registro o el sistema de archivos debe actualizarse al mismo tiempo que se aplica la configuración al IDE. Esto garantiza la coherencia de la configuración y admite escenarios de instancias múltiples de IDE.  
  
2.  Indique a IDE cómo controlar la importación de la configuración.  
  
     Use el argumento devuelto `pfRestartRequired` del método <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> para indicar que al IDE si es necesario reiniciar para aplicar la configuración importada.  
  
     Si la implementación que hace el VSPackage del método <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> devuelve `true`, se solicita al usuario que reinicie el IDE.  
  
## Ejemplo  
 En este ejemplo se muestra cómo importar y exportar datos de configuración.  
  
```  
static const WCHAR c_szFirstSettingName[] = L"FirstSettingName"; static const WCHAR c_szRandomTrashBytes[] = L"RandomTrashBytes"; static const WCHAR c_szRandomTrashLength[] = L"RandomTrashLength"; static const WCHAR c_szBreakPointWindow[] = L"Breakpoints Window"; // -------------------------------------------------------------------------- //    IVsUserSettings methods used for configuration export and import //    Delegate to the right shell object based on the category GUID // -------------------------------------------------------------------------- static const WCHAR c_szFirstSettingName[] = L"FirstSettingName"; static const WCHAR c_szRandomTrashBytes[] = L"RandomTrashBytes"; static const WCHAR c_szRandomTrashLength[] = L"RandomTrashLength"; static const WCHAR c_szBreakPointWindow[] = L"Breakpoints Window"; // Export Settings. STDMETHOD(NeedExport)(WCHAR* pszCategoryGUID, BOOL *pfNeedExport) { if (!pfNeedExport) return E_INVALIDARG; CLSID clsidCategory; HRESULT hr= S_OK; hr = CLSIDFromString(pszCategoryGUID, &clsidCategory); IfFailGo(hr); if (GUID_Profiles_CommandBars == clsidCategory) { *pfNeedExport = TRUE; //Always export Command Bar Configuration }else if (GUID_Profiles_KeyBindings == clsidCategory) { *pfNeedExport = FALSE; //By Default don't export key bindings if (m_fMake_Permanent) *pfNeedExport = TRUE; //Export if user wants current configuration saved. }else{ hr = E_UNEXPECTED; } Error: return hr; } STDMETHOD(ExportSettings)(WCHAR *pszCategoryGUID, IVsSettingsWriter *pSettings) { CLSID clsidCategory; HRESULT hr; hr = CLSIDFromString(pszCategoryGUID, &clsidCategory); IfFailGo(hr); // Delegate to the right internal implementation based on the requested category. if (GUID_Profiles_CommandBars == clsidCategory) { hr = ExportSettings_CommandBars(pSettings); }else if (GUID_Profiles_KeyBindings == clsidCategory) { hr = ExportSettings_KeyBindings(pSettings); }else{ hr = E_UNEXPECTED; } Error: return hr; }; HRESULT ExportSettings_CommandBars(IVsSettingsWriter *pSettings) { if (!pSettings) return E_INVALIDARG; hr = pSettings->WriteSettingString(c_szFirstSettingName, L"Value1"); IfFailGo(hr); int cRandomTrash = 12345; BYTE *pRandomTrash = (BYTE *)VSAlloc(cRandomTrash); if (pRandomTrash){ hr = pSettings->WriteSettingBytes(c_szRandomTrashBytes, pRandomTrash, cRandomTrash); IfFailGo(hr); hr = pSettings->WriteSettingLong(c_szRandomTrashLength, cRandomTrash); IfFailGo(hr); } Error: return hr; }; HRESULT ExportSettings_KeyBindings(IVsSettingsWriter *pSettings) { if (!pSettings) return E_INVALIDARG; hr = pSettings->WriteSettingString(c_szBreakPointWindow, L"Ctrl + Alt + B"); IfFailGo(hr); Error: return hr; }; STDMETHOD(ImportSettings)(WCHAR *pszCategoryGUID, IVsSettingsReader *pSettings, UserSettingsFlags flags, BOOL *pfRestartRequired) { CLSID clsidCategory; HRESULT hr; hr = CLSIDFromString(pszCategoryGUID, &clsidCategory); IfFailGo(hr); // Delegate to the right internal implementation based on the requested category. if (GUID_Profiles_CommandBars == clsidCategory) { hr = ImportSettings_CommandBars(, pSettings, flags, pfRestartRequired); } else if (GUID_Profiles_KeyBindings == clsidCategory) { hr = ImportSettings_KeyBindings( pSettings, flags, pfRestartRequired); } else { hr = E_UNEXPECTED; } Error: return hr; }; // Import Settings. HRESULT ImportSettings_CommandBars(IVsSettingsReader *pSettings, UserSettingsFlags flags, BOOL *pfRestartRequired) { if (!pSettings) return E_INVALIDARG; if (pfRestartRequired) { *pfRestartRequired = FALSE; //Nobody should require a restart!! } CComBSTR bstrFirstSettingName; long lTrashLength = 0; BYTE *pTrashBytes = NULL; // Determines whether to import as an additive operation, or a reset all settings operation. BOOL fResetCompletely = FALSE; if (flags & USF_ResetOnImport) fResetCompletely = TRUE; hr = pSettings->ReadSettingString(c_szFirstSettingName, &bstrFirstSettingName); IfFailGo(hr); hr = pSettings->ReadSettingLong(c_szRandomTrashLength, &lTrashLength); IfFailGo(hr); if (lTrashLength > 0) { pTrashBytes = (BYTE*)VSAlloc(lTrashLength); IfNullMemGo(pTrashBytes); long lDataRead = 0; hr = pSettings->ReadSettingBytes(c_szRandomTrashLength, pTrashBytes, &lDataRead, lTrashLength); IfFailGo(hr); if (lDataRead != lTrashLength) { hr = E_UNEXPECTED; goto Error; } } // Note: before returning these settings should immediately be applied to your personal //            settings store, whether in the registry or the file system. // This write-thru cache methodology is essential to work in multi-instance IDE scenarios. hr = UpdateState_CommandBar(bstrFirstSettingName,lTrashLength,pTrashBytes,lDataRead); Error: return hr; }; HRESULT ImportSettings_KeyBindings(IVsSettingsReader *pSettings, UserSettingsFlags flags, BOOL *pfRestartRequired) { if (!pSettings) return E_INVALIDARG; if (pfRestartRequired) { *pfRestartRequired = FALSE; //Nobody should require a restart!! } CComBSTR bstrBreakPointWindow; // Determines whether to import as an additive operation or a reset all settings operation. BOOL fResetCompletely = FALSE; if (flags & USF_ResetOnImport) fResetCompletely = TRUE; hr = pSettings->ReadSettingString(c_szBreakPointWindow, &bstrBreakPointWindow); IfFailGo(hr); // Note: before returning these settings should immediately be applied to your personal //            settings store, whether in the registry or the file system. // This write-thru cache methodology is essential to work in multi-instance IDE scenarios. hr = UpdateState_KeyBindings(bstrBreakPointWindow); Error: return hr; }  
```  
  
## Vea también  
 [Cómo: Exportar configuración mediante ensamblados de interoperabilidad](../misc/how-to-export-settings-by-using-interop-assemblies.md)   
 [Compatibilidad con la configuración de usuario](../extensibility/internals/support-for-user-settings.md)   
 [Opciones y configuración de usuario de extensión](../extensibility/extending-user-settings-and-options.md)   
 [Personalizar la configuración de desarrollo en Visual Studio](http://msdn.microsoft.com/es-es/22c4debb-4e31-47a8-8f19-16f328d7dcd3)