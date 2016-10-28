# php-pdolib
PDO DB library for Slim Framework

#USAGE

require_once 'vendor/autoload.php';

$dsn = 'mysql:host=your_db_host;dbname=your_db_name;charset=utf8';

$usr = 'your_db_username';

$pwd = 'your_db_password';

$pdo = new \Slim\PDO\Database($dsn, $usr, $pwd);

// SELECT * FROM users WHERE id = ?

$selectStatement = $pdo->select()

->from('users')

->where('id', '=', 1234);

$stmt = $selectStatement->execute();

$data1 = $stmt->fetch(); //return 1 record

$data2 = $stmt->fetchAll(); //returns all records

// INSERT INTO users ( id , usr , pwd ) VALUES ( ? , ? , ? )

$insertStatement = $pdo->insert(array('id', 'usr', 'pwd'))

->into('users')

->values(array(1234, 'your_username', 'your_password'));

$insertId = $insertStatement->execute(false);

// UPDATE users SET pwd = ? WHERE id = ?

$updateStatement = $pdo->update(array('pwd' => 'your_new_password'))

->table('users')

->where('id', '=', 1234);
                       
$affectedRows = $updateStatement->execute();

// DELETE FROM users WHERE id = ?

$deleteStatement = $pdo->delete()

->from('users')

->where('id', '=', 1234);

$affectedRows = $deleteStatement->execute();
