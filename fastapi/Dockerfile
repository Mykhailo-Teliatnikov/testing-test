FROM python:3.9.17

COPY testing-test/fastapi/main.py /main.py

RUN pip install fastapi "uvicorn[standard]"

EXPOSE 8000
EXPOSE 80
WORKDIR /
CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "80"]