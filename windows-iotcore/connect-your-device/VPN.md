---
title: Windows 10 IoT Core는 VPN
author: saraclay
ms.author: saclayt
ms.date: 11/19/2018
ms.topic: article
description: 를 사용 하 고 설치 프로그램을 Windows 10 IoT Core 장치에 대 한 VPN 기능을 구성 하는 방법을 알아봅니다.
keywords: windows iot, VPN, 설치, 장치
ms.openlocfilehash: 94eafcb74a05179a7741cb516b5e7be30b525092
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512974"
---
# <a name="leveraging-vpn-capabilities-for-your-windows-10-iot-core-device"></a><span data-ttu-id="de24b-104">Windows 10 IoT Core 장치에 대 한 VPN 기능을 활용 하 여</span><span class="sxs-lookup"><span data-stu-id="de24b-104">Leveraging VPN capabilities for your Windows 10 IoT Core device</span></span>

<span data-ttu-id="de24b-105">Windows 10 IoT Core VPN 기능을 활용 하려면 아래 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="de24b-105">In order to leverage the VPN capabilities of Windows 10 IoT Core, follow the instructions below.</span></span>

> [!NOTE]
> <span data-ttu-id="de24b-106">대부분의 아래 지침에 맞게 조정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="de24b-106">Most of the instructions below must be adapted.</span></span> <span data-ttu-id="de24b-107">사용자가 연결 되어 있는 VPN 호스트에 특정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="de24b-107">They are specific to the VPN host that the user is connecting to.</span></span> <span data-ttu-id="de24b-108">인증서 사용은 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="de24b-108">The certs used are examples.</span></span>

## <a name="establishing-a-vpn-connection"></a><span data-ttu-id="de24b-109">VPN 연결</span><span class="sxs-lookup"><span data-stu-id="de24b-109">Establishing a VPN connection</span></span> 

1. <span data-ttu-id="de24b-110">필요한 인증서를 구하여 IoT 장치 (예: \vpntest 폴더)에 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="de24b-110">Obtain the necessary certs and copy to your IoT device (e.g. to a \vpntest folder).</span></span>

* <span data-ttu-id="de24b-111">RASTest.pfx</span><span class="sxs-lookup"><span data-stu-id="de24b-111">RASTest.pfx</span></span>
* <span data-ttu-id="de24b-112">IssuingCA.crl</span><span class="sxs-lookup"><span data-stu-id="de24b-112">IssuingCA.crl</span></span>
* <span data-ttu-id="de24b-113">RootCA.crl</span><span class="sxs-lookup"><span data-stu-id="de24b-113">RootCA.crl</span></span>

2. <span data-ttu-id="de24b-114">로컬 컴퓨터 인증서를 적용 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="de24b-114">Apply local machine certs a.</span></span> <span data-ttu-id="de24b-115">관리자 권한으로 장치에 대 한 PowerShell</span><span class="sxs-lookup"><span data-stu-id="de24b-115">PowerShell into device as administrator</span></span>

```powershell
certmgr -add .\IssuingCA.crl -r localmachine -s root
certmgr -add .\RootCA.crl -r localmachine -s root
```

3. <span data-ttu-id="de24b-116">사용자 인증서를 적용 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="de24b-116">Apply user certs a.</span></span> <span data-ttu-id="de24b-117">SSH를 사용 하 여 "DefaultAccount"으로 IoT 장치에 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="de24b-117">Login to the IoT Device using SSH as "DefaultAccount".</span></span>
<span data-ttu-id="de24b-118">b.</span><span class="sxs-lookup"><span data-stu-id="de24b-118">b.</span></span> <span data-ttu-id="de24b-119">명령 프롬프트에서 "PowerShell"을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="de24b-119">From the command prompt, type "PowerShell".</span></span>
<span data-ttu-id="de24b-120">다.</span><span class="sxs-lookup"><span data-stu-id="de24b-120">c.</span></span> <span data-ttu-id="de24b-121">("기본 계정"으로 로그인) 하는 동안 PowerShell에서 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="de24b-121">Issue the following commands from PowerShell (while logged in as "Default Account"):</span></span>

```powershell
$mypwd = ConvertTo-SecureString -String "<password>" -Force -AsPlainText
import-pfxcertificate -FilePath RasTest.pfx -CertStoreLocation cert:currentUser\my -Password $mypwd

Cert -add .\IssuingCA.crl -r currentuser -s my
certmgr -add .\RootCA.crl -r currentuser -s my
```

4. <span data-ttu-id="de24b-122">수정 호스트 파일 c:\windows\system32\driverS\etc\hosts 파일 (예: 아래;)에 항목 추가</span><span class="sxs-lookup"><span data-stu-id="de24b-122">Fix hosts file Add an entry into c:\windows\system32\driverS\etc\hosts file (example shown below);</span></span>

> |    |    |    |
> |----|----| ---|
> | <span data-ttu-id="de24b-123">10.10.10.10</span><span class="sxs-lookup"><span data-stu-id="de24b-123">10.10.10.10</span></span> | <span data-ttu-id="de24b-124">MyVPN.DomainName.org</span><span class="sxs-lookup"><span data-stu-id="de24b-124">MyVPN.DomainName.org</span></span> | <span data-ttu-id="de24b-125">필요에 따라 IP 주소 및 도메인 이름으로 대체</span><span class="sxs-lookup"><span data-stu-id="de24b-125">Replace with IP address and domain name as needed</span></span> |

5. <span data-ttu-id="de24b-126">빌드 VPN 테스트 응용 프로그램 소스 코드에서 "MyVPN.DomainName.org" 대체 합니다.</span><span class="sxs-lookup"><span data-stu-id="de24b-126">Build the VPN test app Replace the "MyVPN.DomainName.org" in the source code.</span></span> <span data-ttu-id="de24b-127">필요에 따라 추가 보강 합니다.</span><span class="sxs-lookup"><span data-stu-id="de24b-127">Augment further as needed.</span></span>

6. <span data-ttu-id="de24b-128">아래에 코드 배포는 Windows 10 IoT 장치에 "시작 및 중지 하는 VPN 연결" 섹션.</span><span class="sxs-lookup"><span data-stu-id="de24b-128">Deploy the code below in the "Starting and stopping a VPN Connection" section to the Windows 10 IoT device.</span></span>
<span data-ttu-id="de24b-129">임의의 "프로필 이름을"를 입력 하 고 "VPN에 연결" 단추를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="de24b-129">Enter an arbitrary "Profile name" and press the "Connect to VPN" button.</span></span> 


## <a name="starting-and-stopping-a-vpn-connection"></a><span data-ttu-id="de24b-130">시작 하 고 VPN 연결을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="de24b-130">Starting and stopping a VPN connection</span></span>

<span data-ttu-id="de24b-131">아래 코드를 사용 하 여 시작 하 고 VPN 연결을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="de24b-131">Use the code below to start and stop a VPN connection.</span></span>

```csharp

  private async Task ConnectVPNProfile()
        {
            string vpnProfileName = "MyVPNProfileName";

            string[] epdg = { "MyVPN.DomainName.org" };
            VpnManagementErrorStatus status = VpnManagementErrorStatus.Ok;
            IAsyncOperation<VpnManagementErrorStatus> op;

            var vpnMa = new VpnManagementAgent();
            var vpnProfile = new VpnNativeProfile();
            vpnProfile.AlwaysOn = true;
            vpnProfile.ProfileName = vpnProfileName;
            vpnProfile.RequireVpnClientAppUI = true;
            vpnProfile.RememberCredentials = true;
            vpnProfile.RoutingPolicyType = VpnRoutingPolicyType.SplitRouting;
            vpnProfile.TunnelAuthenticationMethod = VpnAuthenticationMethod.Eap;
            vpnProfile.UserAuthenticationMethod = VpnAuthenticationMethod.Eap;
            foreach (var s in epdg)
            {
                vpnProfile.Servers.Add(s);
            }

            vpnProfile.EapConfiguration = GetEapXmlString();

            // Adds the profile using the management api.
           status = await vpnMa.AddProfileFromObjectAsync(vpnProfile);
            Debug.WriteLine($"Add profile: {status}");
            TextBlockLog.Text += $"Add profile: {status}\r\n";

            await Task.Delay(1000);

            op = vpnMa.ConnectProfileAsync(vpnProfile);
            status = await op;
            Debug.WriteLine($"Connect succeeded: {status}");
            TextBlockLog.Text += $"Connect profile: {status}\r\n";


        }


  public static string GetEapXmlString()
        {
            //string template = "<EapHostConfig xmlns=\"http://www.microsoft.com/provisioning/EapHostConfig\"><EapMethod><Type xmlns=\"http://www.microsoft.com/provisioning/EapCommon\">25</Type><VendorId xmlns=\"http://www.microsoft.com/provisioning/EapCommon\">0</VendorId><VendorType xmlns=\"http://www.microsoft.com/provisioning/EapCommon\">0</VendorType><AuthorId xmlns=\"http://www.microsoft.com/provisioning/EapCommon\">0</AuthorId></EapMethod><Config xmlns=\"http://www.microsoft.com/provisioning/EapHostConfig\"><Eap xmlns=\"http://www.microsoft.com/provisioning/BaseEapConnectionPropertiesV1\"><Type>25</Type><EapType xmlns=\"http://www.microsoft.com/provisioning/MsPeapConnectionPropertiesV1\"><ServerValidation><DisableUserPromptForServerValidation>true</DisableUserPromptForServerValidation><ServerNames></ServerNames><TrustedRootCA>d2 d3 8e ba 60 ca a1 c1 20 55 a2 e1 c8 3b 15 ad 45 01 10 c2 </TrustedRootCA><TrustedRootCA>d1 76 97 cc 20 6e d2 6e 1a 51 f5 bb 96 e9 35 6d 6d 61 0b 74 </TrustedRootCA></ServerValidation><FastReconnect>true</FastReconnect><InnerEapOptional>false</InnerEapOptional><Eap xmlns=\"http://www.microsoft.com/provisioning/BaseEapConnectionPropertiesV1\"><Type>13</Type><EapType xmlns=\"http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV1\"><CredentialsSource><CertificateStore><SimpleCertSelection>true</SimpleCertSelection></CertificateStore></CredentialsSource><ServerValidation><DisableUserPromptForServerValidation>true</DisableUserPromptForServerValidation><ServerNames></ServerNames><TrustedRootCA>d2 d3 8e ba 60 ca a1 c1 20 55 a2 e1 c8 3b 15 ad 45 01 10 c2 </TrustedRootCA><TrustedRootCA>d1 76 97 cc 20 6e d2 6e 1a 51 f5 bb 96 e9 35 6d 6d 61 0b 74 </TrustedRootCA></ServerValidation><DifferentUsername>false</DifferentUsername><PerformServerValidation xmlns=\"http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2\">true</PerformServerValidation><AcceptServerName xmlns=\"http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2\">false</AcceptServerName><TLSExtensions xmlns=\"http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2\"><FilteringInfo xmlns=\"http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV3\"><EKUMapping><EKUMap><EKUName>AAD Conditional Access</EKUName><EKUOID>1.3.6.1.4.1.311.87</EKUOID></EKUMap></EKUMapping><ClientAuthEKUList Enabled=\"true\"><EKUMapInList><EKUName>AAD Conditional Access</EKUName></EKUMapInList></ClientAuthEKUList></FilteringInfo></TLSExtensions></EapType></Eap><EnableQuarantineChecks>false</EnableQuarantineChecks><RequireCryptoBinding>true</RequireCryptoBinding><PeapExtensions><PerformServerValidation xmlns=\"http://www.microsoft.com/provisioning/MsPeapConnectionPropertiesV2\">true</PerformServerValidation><AcceptServerName xmlns=\"http://www.microsoft.com/provisioning/MsPeapConnectionPropertiesV2\">false</AcceptServerName></PeapExtensions></EapType></Eap></Config></EapHostConfig>";
            string template = "<EapHostConfig xmlns =\"http://www.microsoft.com/provisioning/EapHostConfig\"><EapMethod><Type xmlns=\"http://www.microsoft.com/provisioning/EapCommon\">13</Type><VendorId xmlns=\"http://www.microsoft.com/provisioning/EapCommon\">0</VendorId><VendorType xmlns=\"http://www.microsoft.com/provisioning/EapCommon\">0</VendorType><AuthorId xmlns=\"http://www.microsoft.com/provisioning/EapCommon\">0</AuthorId></EapMethod><Config xmlns=\"http://www.microsoft.com/provisioning/EapHostConfig\"><Eap xmlns=\"http://www.microsoft.com/provisioning/BaseEapConnectionPropertiesV1\"><Type>13</Type><EapType xmlns=\"http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV1\"><CredentialsSource><CertificateStore><SimpleCertSelection>true</SimpleCertSelection></CertificateStore></CredentialsSource><ServerValidation><DisableUserPromptForServerValidation>false</DisableUserPromptForServerValidation><ServerNames></ServerNames><TrustedRootCA>b6 ea bf ba 48 be 09 c9 50 4f c6 ea 9b f5 74 dc a9 01 56 62 </TrustedRootCA></ServerValidation><DifferentUsername>false</DifferentUsername><PerformServerValidation xmlns=\"http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2\">false</PerformServerValidation><AcceptServerName xmlns=\"http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2\">false</AcceptServerName><TLSExtensions xmlns=\"http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2\"><FilteringInfo xmlns=\"http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV3\"><CAHashList Enabled=\"true\"><IssuerHash>b6 ea bf ba 48 be 09 c9 50 4f c6 ea 9b f5 74 dc a9 01 56 62 </IssuerHash></CAHashList></FilteringInfo></TLSExtensions></EapType></Eap></Config></EapHostConfig>";
            //TODO: Create propper XML here
            string result = template;

            return result;
        }
```






