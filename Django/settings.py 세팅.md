
TEMPLATES = {

  'DIRS': [os.path.join(BASE_DIR, '앱명/templates')] -> 프로젝트명/templates로 해도 되는데, 그건 사람 마음.
}

- 템플릿이나 뷰에서 상대 경로로 주소 쓰면, TEMPLATES의 DIR에 있는 폴더를 기준으로 시작된 상대 경로로 템플릿 렌더링 함.
