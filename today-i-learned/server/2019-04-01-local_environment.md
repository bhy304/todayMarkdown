# 2019-04-01-Local\_Environment

## **Tacotron English Dataset\_Windows Local Environment**

## 1. Installing dependencies

1-1. Git fork and clone [tacotron](https://github.com/keithito/tacotron)

1-2. python 3.6 버전으로 가상환경 구축

```text
  conda create --name "tacotron" python=3.6
activate tacotron
```

1-3. pip install tensorflow==1.3.0  
※ This code works with TensorFlow 1.3 and later.

1-4. pip install -r requirements.txt  
※ Error 발생으로 \#numpy==1.14.3, \#scipy==0.19.0 주석 처리

```text
  pip install -U numpy
  pip install -U scipy
```

## 2. Using a pre-trained model

2-1. Download and unpack a model:  
[http://data.keithito.com/data/speech/tacotron-20180906.tar.gz](http://data.keithito.com/data/speech/tacotron-20180906.tar.gz) 다운로드 후 압축 풀기 → 프로젝트 폴더로 파일 이동

2-2. Run the demo server:

```text
 python demo_server.py --checkpoint tacotron-20180906/model.ckpt
```

2-3. Point your browser at localhost:9000  
브라우저에서 localhost:9000 접속

## 3. Training

1. Download a speech dataset. The following are supported out of the box:   [LJ Speech \(Public Domain\)](https://keithito.com/LJ-Speech-Dataset/)
2. Unpack the dataset into ~/tacotron
3. Preprocess the data :

   ```text
    python preprocess.py --dataset ljspeech
   ```

※ FileNotFoundError : No such file or directory 에러 발생 시:

* process.py : os.path.expanduser 경로 수정!

  ```text
    def main():
      parser.add_argument('--base_dir', default=os.path.expanduser('**/git/tacotron**'))
  ```

* train.py : os.path.expanduser 경로 수정!

  ```text
    def main():
      parser.add_argument('--base_dir', default=os.path.expanduser('**/git/tacotron**'))
  ```

* Train a model

  ```text
   python train.py
  ```

## 5. Monitor with Tensorboard \(optional\)

5-1. tensorboard --logdir /git/tacotron/logs-tacotron ※ logdir 경로 주의!!!!

5-2. [http://desktop-eh6ita6:6006/](http://desktop-eh6ita6:6006/) 접속하면 모니터링 가능!

