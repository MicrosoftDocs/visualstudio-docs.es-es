---
title: Registro de un evaluador de expresiones Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluators, registering
ms.assetid: 236be234-e05f-4ad8-9200-24ce51768ecf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 600f7c8a2e2957cddf23ccc82b0872617e491940
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713208"
---
# <a name="register-an-expression-evaluator"></a>Registrar un evaluador de expresiones
> [!IMPORTANT]
> En Visual Studio 2015, esta forma de implementar evaluadores de expresiones está en desuso. Para obtener información sobre la implementación de evaluadores de expresiones CLR, vea Evaluadores de [expresiones CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y Ejemplo de evaluador de [expresiones administradas](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 El evaluador de expresiones (EE) debe registrarse como un generador de clases con el entorno COM de Windows y Visual Studio. Un EE se configura como un archivo DLL para que se inyecte en el espacio de direcciones del motor de depuración (DE) o en el espacio de direcciones de Visual Studio, dependiendo de la entidad que cree una instancia de EE.

## <a name="managed-code-expression-evaluator"></a>Evaluador de expresiones de código administrado
 Un eE de código administrado se implementa como una biblioteca de clases, que es un archivo DLL que se registra con el entorno COM, normalmente iniciado por una llamada al programa VSIP, *regpkg.exe*. El proceso real de escribir las claves del Registro para el entorno COM se controla automáticamente.

 Un método de la clase <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute>principal se marca con , lo que indica que se debe llamar al método cuando el archivo DLL se está registrando con COM. Este método de `RegisterClass`registro, a menudo llamado , realiza la tarea de registrar el archivo DLL con Visual Studio. Un `UnregisterClass` correspondiente (marcado <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute>con el ), `RegisterClass` deshace los efectos de cuando se desinstala el archivo DLL.
Las mismas entradas de registro se realizan como para un EE escrito en código no administrado; la única diferencia es que no `SetEEMetric` hay ninguna función auxiliar como hacer el trabajo por usted. A continuación se muestra un ejemplo del proceso de registro y cancelación del registro.

### <a name="example"></a>Ejemplo
 La siguiente función muestra cómo un código administrado EE se registra y anula el registro con Visual Studio.

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
 El archivo DLL de `DllRegisterServer` EE implementa la función para registrarse con el entorno COM, así como Visual Studio.

> [!NOTE]
> Puede encontrar el código de registro de ejemplo de código MyCEE en el archivo *dllentry.cpp*, que se encuentra en la instalación de VSIP en EnVSDK- MyCPkgs-MyCEE.

### <a name="dll-server-process"></a>Proceso del servidor DLL
 Al registrar el EE, el servidor DLL:

1. Registra su generador `CLSID` de clases según las convenciones COM normales.

2. Llama a `SetEEMetric` la función auxiliar para registrar con Visual Studio las métricas EE que se muestran en la tabla siguiente. La `SetEEMetric` función y las métricas especificadas de la siguiente manera forman parte de la biblioteca *dbgmetric.lib.* Consulte Aplicaciones auxiliares del [SDK para la depuración](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) para obtener más información.

    |Métrica|Descripción|
    |------------|-----------------|
    |`metricCLSID`|`CLSID`de la fábrica de clases EE|
    |`metricName`|Nombre del EE como una cadena visible|
    |`metricLanguage`|El nombre del idioma que el EE está diseñado para evaluar|
    |`metricEngine`|`GUID`s de los motores de depuración (DE) que funcionan con este EE|

    > [!NOTE]
    > El `metricLanguage``GUID` identifica el idioma por nombre, `guidLang` pero `SetEEMetric` es el argumento para que seleccione el idioma. Cuando el compilador genera el archivo de `guidLang` información de depuración, debe escribir el adecuado para que el DE sepa qué EE usar. El DE normalmente pide al `GUID`proveedor de símbolos para este idioma, que se almacena en el archivo de información de depuración.

3. Se registra en Visual Studio mediante la creación de\\claves en HKEY_LOCAL_MACHINE, SOFTWARE, Microsoft, VisualStudio*X.Y*, donde *X.Y* es la versión de Visual Studio con la que registrarse.

### <a name="example"></a>Ejemplo
 La siguiente función muestra cómo un código no administrado (C++) EE se registra y anula el registro con Visual Studio.

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
- [Escribir un evaluador de expresiones CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [Ayudantes del SDK para la depuración](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
