# SSH key
proyecto privado Github


## Comandos para generar la SSH Key
ssh-keygen -t rsa -b 4096 -C "mimosa@kausana.cl"
ssh-add ~/.ssh/id_rsa


## Ingresarlo en la cuenta de git
- Settings
- SSH and GPG keys
- New SSH key

## Ejemplo de agregado

ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAACAQCTa1S+VNBtjwZfvtMxgo3utc2J9ViyoGizrUn2cPAoYmSGgWpbK9JiH6AY6QUmpIFmbh3CYqZ3tHm1cZmMU2eUTFW+zODE7S0wGLaONZRs07ClwtI9av8tyuCeuVITIhOh0OF80/N7avKC6kLfiwdkxzKF7iez/dYlOdC+pptT2jd3AJeJKlbaQOaCeyxvGGilBXheAczIOi1PTC6R9OiG5hoFZE7+zsXGekfWljNQBdQl3zN+wzksMLvSoCWKkdVgYZ+KeVTRd0VyO6Pz63wEwZq2gUr5Ejq4d/XtHpBYUqvdpwHGty55ILkX18eKzS+1qJwAaNVIFRkKFIyCAnX9SqZLgXiER6Grde/w/IlSBRsHscDjKCC/IS1LdZOdDb8p9vVwg6apDEX5jeE1A61YRqczvsDgc4tRPgRd64NoXFs7LHEvbgqS8fNK4meazLErEHKu2RzC23mDFj2jgMCu44Kv/vN87ovsomXf3OMmbqvVjvJjK4Lld54nYBJ+h26tUTfKxr1kLi1BrcAsa+BNFFd7MIkJK/uul/nL5pQItrM9SlvLOlxv4yePPBPCfwRqHgC7Fg1QYThfVNBZIxX1I/lu4caOBu6XD4kcLSDfSmJKpteZtRNaRGUlvHuyF+3IvYAJGZaoJ1zsyr+uzCf/0hD56aKrRN4nO+R01fUKHw== mimosa@kausana.cl


# Agregar identidad global
git config --global user.name "Mimosa Server"
git config --global user.email mimosa@kausana.cl

# Multiple cuenta
https://gist.github.com/oanhnn/80a89405ab9023894df7

git remote set-url origin git@github-personal:pedroIgnacioM/docs.git
git config user.email "pedro.ignaciom95@gmail.com"
git config user.name  "PedroM Mac"