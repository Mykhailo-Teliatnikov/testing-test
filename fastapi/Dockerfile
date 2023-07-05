FROM python:3.9.17

COPY main.py /main.py

RUN pip install fastapi "uvicorn[standard]"

EXPOSE 8000
WORKDIR /
CMD ["uvicorn", "main:app", "--reload"]