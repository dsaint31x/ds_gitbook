# Conda 명령어

## env 생성.

```
conda create -n [env_name] python=[version]
```

* example
```
conda create -n gitbook python=3.7
```

## env 활성화

해당 env에서 작업시작.

```
conda activate [env_name]
```

* example
```
conda activate gitbook
```

## env 에서 나오기.(비활성화)

현재 env에서 나오기.

```
conda deactivate
```

