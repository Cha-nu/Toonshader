# Toonshader

언리얼 엔진 5.8에서 툰 셰이딩을 공부하며 만든 머티리얼 모음입니다.
명조: 워더링 웨이브의 캐릭터 릴리를 기준으로 맞췄습니다.

시연 영상: https://youtu.be/pODmPnxIy_Y

## 고지

- 셰이더 공부를 위한 비상업적 팬메이드 작업입니다.
- 캐릭터 모델과 텍스처의 저작권은 Kuro Games에 있으며, 이 저장소에는 **포함하지 않습니다.**
- 문제가 되는 경우 알려 주시면 내리겠습니다.

## 들어 있는 것

머티리얼 에셋(`.uasset`)만 있습니다. 모델, 텍스처, 애니메이션, 레벨, 블루프린트는 없습니다.

| 폴더 | 내용 |
| --- | --- |
| `Content/Lily/Toon2` | 현재 쓰는 구성. 후처리 `PP_Toon`, 몸 `MM_ToonLit`, 얼굴 `MM_ToonFace`, 눈 `MM_ToonEye`, 눈썹 비침 `M_BrowSeeThrought` |
| `Content/Lily/Toon/Outline` | 외곽선 `M_ToonOutline`과 부위별 인스턴스 |
| `Content/Lily/Toon` | 처음 만든 Unlit 방식 셰이더 (비교용) |
| `Content/Lily/Material` | 모델을 가져올 때 생긴 원본 인스턴스 |
| `Content/Material/PP` | 후처리 외곽선 실험 |

## 열어 볼 때

- 텍스처가 없어서 머티리얼 인스턴스의 텍스처 슬롯은 비어 있습니다. 노드 구성과 파라미터를 참고하는 용도입니다.
- `PP_Toon`은 캐릭터 메시의 Custom Depth Stencil 값이 1인 픽셀에만 적용됩니다. 프로젝트 설정에서 Custom Depth-Stencil Pass를 `Enabled with Stencil`로 두어야 합니다.
- 흔들림에는 [Kawaii Physics](https://github.com/pafuhana1213/KawaiiPhysics) 플러그인을 썼습니다. 애니메이션 블루프린트는 이 저장소에 없습니다.

## 제작 과정

1. [셀 셰이딩의 원리](https://cha-nu.github.io/posts/toon-shading-1/)
2. [언리얼 머티리얼 구현](https://cha-nu.github.io/posts/toon-shading-2/)
3. [디테일과 색감](https://cha-nu.github.io/posts/toon-shading-3/)
4. [애니메이션과 Kawaii Physics](https://cha-nu.github.io/posts/toon-shading-4/)
5. [원리와 HLSL](https://cha-nu.github.io/posts/toon-shading-5/)
6. [흰 조명 맞추기와 회고](https://cha-nu.github.io/posts/toon-shading-6/)

## 알려진 한계

- 앞머리 하이라이트의 모양이 원작과 다릅니다.
- 조명 색 반영(`PP_Toon`의 `LightInfluence`)은 Directional Light만 읽으며, 기본값은 0(끔)입니다.
- 달릴 때 치마와 리본 끈이 몸을 뚫는 문제는 해결하지 못했습니다.
