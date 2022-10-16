# 정답
* _helpers.tpl에 define을 사용하여 템플릿 정의
| 참고자료: https://helm.sh/docs/chart_template_guide/named_templates/#declaring-and-using-templates-with-define-and-template

```sh
{{- define "names" }}
{{- .Release.Name -}}-named-template
{{- end -}}
```
* 정의한 template을 불러올 때는 define 또는 include 사용

# template과 include차이
* template은 action타입이어서 파이프라인 연동 불가
```sh
# 아래 코드는 오류
name: {{ template "names" . | quote  }}
```

* include는 function타입이어서 파이프라인 연동 가능
```sh
name: {{ include "names" . | quote  }}
```

# 오픈소스 활용 예:
* [elasticsearch](https://github.com/elastic/helm-charts/blob/main/elasticsearch/templates/statefulset.yaml#L5)
* [promtheus-operator](https://github.com/prometheus-community/helm-charts/blob/main/charts/kube-prometheus-stack/templates/prometheus-operator/deployment.yaml#L7)
* [argocd repo-server](https://github.com/argoproj/argo-helm/blob/main/charts/argo-cd/templates/argocd-repo-server/deployment.yaml#L4)