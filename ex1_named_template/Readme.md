# 문제
* template/deployment.yaml에 사용한 **{{ .Release.Name }}-named-template**을 템플릿으로 정의하시오.
* 템플릿은 _helpers.tpl에 정의하세요
* 템플릿으로 정의해야 하는 이유는 공통으로 사용한 것을 묶어서 관리를 편하게 하기 위해서입니다.

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: {{ .Release.Name }}-named-template
...

```