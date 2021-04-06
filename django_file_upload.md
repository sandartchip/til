
- Django에서 input type=file 타입으로 입력된 파일데이터는, **InMemoryUploadedFile** 타입으로 저장된다.

file객체의 이름을 가져오려면
'''
 file_form.cleaned_data["file"].name
'''


- os.path.join은  \으로 붙는다.
- 예시) job_id\gene_information.txt



