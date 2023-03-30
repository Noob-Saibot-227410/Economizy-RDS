import boto3
# Região onde encontra-se minha instância
region = 'us-east-1'
# Qual tipo de serviço pois poderia ser ec2
client = boto3.client('rds')

# Nome da instância se for mais de uma separar por virgula
my_instances = ['MINHAINSTANCIA']

def lambda_handler(event, context):

# Buscando todas as instancias
    for instance in my_instances:
# Funcao de stop para ligar basta alterar o stop pelo start
	response = client.stop_db_instance(DBInstanceIdentifier=instance)
	print 'RDS Stopped: ' +instance