---
title: Registrar un evaluador de expresiones | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluators, registering
ms.assetid: 236be234-e05f-4ad8-9200-24ce51768ecf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b3e764220fe5fe01e20b66af403dfd8b423e34e7
ms.sourcegitcommit: f685fa5e2df9dc307bf1230dd9dc3288aaa408b5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2018
ms.locfileid: "36234031"
---
# <a name="registering-an-expression-evaluator"></a>Registro de un evaluador de expresiones
> [!IMPORTANT]
>  En Visual Studio 2015, esta forma de implementar los evaluadores de expresión está en desuso. Para obtener información sobre la implementación de evaluadores de expresión de CLR, vea [evaluadores de expresiones CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y [Managed expresión del evaluador de expresiones Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 El evaluador de expresiones (EE) debe registrarse como un generador de clases con el entorno COM de Windows y Visual Studio. Un EE se implementa como un archivo DLL para que se puede insertarse en el espacio de direcciones del motor DE depuración o el espacio de direcciones de Visual Studio, dependiendo de qué entidad crea una instancia de lo EE.  
  
## <a name="managed-code-expression-evaluator"></a>Evaluador de expresiones de código administrado  
 Un código administrado EE se implementa como una biblioteca de clases, que es un archivo DLL que se registra con el entorno COM, normalmente se inician haciendo una llamada al programa VSIP, **regpkg.exe**. El proceso real de escribir las claves del registro para el entorno COM se controla automáticamente.  
  
 Un método de la clase principal está marcado con <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute>, lo que indica que el método es que se llamará cuando el archivo DLL es que se va a registrar con COM. Este método de registro, a menudo llamado `RegisterClass`, realiza la tarea de registrar la DLL con Visual Studio. Correspondiente `UnregisterClass` (marcados con el <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute>), deshace los efectos de `RegisterClass` cuando se desinstala el archivo DLL.  
  
 Se realizan las mismas entradas del registro que para un EE escrito en código no administrado; la única diferencia es que no hay ninguna función auxiliar como `SetEEMetric` para hacer el trabajo por usted. Un ejemplo de este proceso de registro o anulación del registro tiene este aspecto:  
  
### <a name="example"></a>Ejemplo  
 Esta función muestra cómo un código administrado EE registra y anula su propio registro con Visual Studio.  
  
```csharp  
namespace EEMC  
{  
    [GuidAttribute("462D4A3D-B257-4AEE-97CD-5918C7531757")]  
    public class EEMCClass : IDebugExpressionEvaluator  
    {  
        #region Register and unregister.  
        private static Guid guidMycLang = new Guid("462D4A3E-B257-4AEE-97CD-5918C7531757");  
        private static string languageName = "MyC";  
        private static string eeName = "MyC Expression Evaluator";  
  
        private static Guid guidMicrosoftVendor = new Guid("994B45C4-E6E9-11D2-903F-00C04FA302A1");  
        private static Guid guidCOMPlusOnlyEng = new Guid("449EC4CC-30D2-4032-9256-EE18EB41B62B");  
        private static Guid guidCOMPlusNativeEng = new Guid("92EF0900-2251-11D2-B72E-0000F87572EF");  
  
        /// <summary>  
        /// Register the expression evaluator.  
        /// Set "project properties/configuration properties/build/register for COM interop" to true.  
        /// </summary>  
         [ComRegisterFunctionAttribute]  
        public static void RegisterClass(Type t)  
        {  
            // Get Visual Studio version (set by regpkg.exe)  
            string hive = Environment.GetEnvironmentVariable("EnvSdk_RegKey");  
            string s = @"SOFTWARE\Microsoft\VisualStudio\"  
                        + hive  
                        + @"\AD7Metrics\ExpressionEvaluator";  
  
            RegistryKey rk = Registry.LocalMachine.CreateSubKey(s);  
            if (rk == null)  return;  
  
            rk = rk.CreateSubKey(guidMycLang.ToString("B"));  
            rk = rk.CreateSubKey(guidMicrosoftVendor.ToString("B"));  
            rk.SetValue("CLSID", t.GUID.ToString("B"));  
            rk.SetValue("Language", languageName);  
            rk.SetValue("Name", eeName);  
  
            rk = rk.CreateSubKey("Engine");  
            rk.SetValue("0", guidCOMPlusOnlyEng.ToString("B"));  
            rk.SetValue("1", guidCOMPlusNativeEng.ToString("B"));  
        }  
        /// <summary>  
        /// Unregister the expression evaluator.  
        /// </summary>  
         [ComUnregisterFunctionAttribute]  
        public static void UnregisterClass(Type t)  
        {  
            // Get Visual Studio version (set by regpkg.exe)  
            string hive = Environment.GetEnvironmentVariable("EnvSdk_RegKey");  
            string s = @"SOFTWARE\Microsoft\VisualStudio\"  
                        + hive  
                        + @"\AD7Metrics\ExpressionEvaluator\"  
                        + guidMycLang.ToString("B");  
            RegistryKey key = Registry.LocalMachine.OpenSubKey(s);  
            if (key != null)  
            {  
                key.Close();  
                Registry.LocalMachine.DeleteSubKeyTree(s);  
            }  
        }  
    }  
}  
```  
  
## <a name="unmanaged-code-expression-evaluator"></a>Evaluador de expresiones de código no administrado  
 La DLL EE implementa el `DllRegisterServer` función registrarse a sí mismo con el entorno COM, así como Visual Studio.  
  
> [!NOTE]
>  El código de registro de ejemplo de código MyCEE puede encontrarse en el archivo dllentry.cpp, que se encuentra en la instalación de VSIP bajo EnVSDK\MyCPkgs\MyCEE.  
  
### <a name="dll-server-process"></a>Proceso de servidor DLL  
 Al registrar el EE, el servidor DLL:  
  
1.  Registra el generador de clases `CLSID` según las convenciones de COM normales.  
  
2.  Llama a la función auxiliar `SetEEMetric` para registrar con Visual Studio, las métricas EE se muestra en la tabla siguiente. La función `SetEEMetric` y las métricas especificadas a continuación son parte de la biblioteca dbgmetric.lib. Consulte [aplicaciones auxiliares de SDK para depuración](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) para obtener más información.  
  
    |Métrica|Descripción|  
    |------------|-----------------|  
    |`metricCLSID`|`CLSID` de la fábrica de clase EE|  
    |`metricName`|Nombre de lo EE como una cadena que se puede mostrar|  
    |`metricLanguage`|El nombre del lenguaje que es el EE diseñado para evaluar|  
    |`metricEngine`|`GUID`s de los motores de depuración (DE) que funcionan con este EE|  
  
    > [!NOTE]
    >  El `metricLanguage``GUID` identifica el idioma por nombre, pero es el `guidLang` argumento `SetEEMetric` que selecciona el idioma. Cuando el compilador genera el archivo de información de depuración, debe escribir adecuado `guidLang` para que la DE sepa qué EE para usar. La DE pide normalmente el proveedor de símbolos para este idioma `GUID`, que está almacenado en el archivo de información de depuración.  
  
3.  Se registra con Visual Studio mediante la creación de claves en HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*X.Y*, donde *X.Y* es la versión de Visual Studio para registrarse.  
  
### <a name="example"></a>Ejemplo  
 Esta función muestra cómo un código no administrado (C++) EE registra y anula su propio registro con Visual Studio.  
  
```cpp  
/*---------------------------------------------------------  
  Registration  
-----------------------------------------------------------*/  
#ifndef LREGKEY_VISUALSTUDIOROOT  
    #define LREGKEY_VISUALSTUDIOROOT L"Software\\Microsoft\\VisualStudio\\8.0"  
#endif  
  
static HRESULT RegisterMetric( bool registerIt )  
{  
    // check where we should register  
    const ULONG cchBuffer = _MAX_PATH;  
    WCHAR wszRegistrationRoot[cchBuffer];  
    DWORD cchFreeBuffer = cchBuffer - 1;  
    wcscpy(wszRegistrationRoot, LREGKEY_VISUALSTUDIOROOT_NOVERSION);  
    wcscat(wszRegistrationRoot, L"\\");  
  
    // this is Environment SDK specific  
    // we check for  EnvSdk_RegKey environment variable to  
    // determine where to register  
    DWORD cchDefRegRoot = lstrlenW(LREGKEY_VISUALSTUDIOROOT_NOVERSION) + 1;  
    cchFreeBuffer = cchFreeBuffer - cchDefRegRoot;  
    DWORD cchEnvVarRead = GetEnvironmentVariableW(  
        /* LPCTSTR */ L"EnvSdk_RegKey", // environment variable name  
        /* LPTSTR  */ &wszRegistrationRoot[cchDefRegRoot],// buffer for variable value  
        /* DWORD   */ cchFreeBuffer);// size of buffer  
    if (cchEnvVarRead >= cchFreeBuffer)  
        return E_UNEXPECTED;  
    // If the environment variable does not exist then we must use   
    // LREGKEY_VISUALSTUDIOROOT which has the version number.  
    if (0 == cchEnvVarRead)  
        wcscpy(wszRegistrationRoot, LREGKEY_VISUALSTUDIOROOT);  
  
    if (registerIt)  
    {  
        SetEEMetric(guidMycLang,  
                    guidMicrosoftVendor,  
                    metricCLSID,  
                    CLSID_MycEE,  
                    wszRegistrationRoot );  
        SetEEMetric(guidMycLang,  
                    guidMicrosoftVendor,  
                    metricName,  
                    GetString(IDS_INFO_MYCDESCRIPTION),  
                    wszRegistrationRoot );  
        SetEEMetric(guidMycLang,  
                    guidMicrosoftVendor,  
                    metricLanguage, L"MyC",  
                    wszRegistrationRoot);  
  
        GUID engineGuids[2];  
        engineGuids[0] = guidCOMPlusOnlyEng;  
        engineGuids[1] = guidCOMPlusNativeEng;  
        SetEEMetric(guidMycLang,  
                    guidMicrosoftVendor,  
                    metricEngine,  
                    engineGuids,  
                    2,  
                    wszRegistrationRoot);  
    }  
    else  
    {  
        RemoveEEMetric( guidMycLang,  
                        guidMicrosoftVendor,  
                        metricCLSID,  
                        wszRegistrationRoot);  
        RemoveEEMetric( guidMycLang,  
                        guidMicrosoftVendor,  
                        metricName,  
                        wszRegistrationRoot );  
        RemoveEEMetric( guidMycLang,  
                        guidMicrosoftVendor,  
                        metricLanguage,  
                        wszRegistrationRoot );  
        RemoveEEMetric( guidMycLang,  
                        guidMicrosoftVendor,  
                        metricEngine,  
                        wszRegistrationRoot );  
    }  
  
    return S_OK;  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [Escribir un evaluador de expresiones CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Aplicaciones auxiliares de SDK para la depuración](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
