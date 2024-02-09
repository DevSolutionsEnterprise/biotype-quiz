<script setup>
import { ref, computed } from 'vue'
import YouTube from 'vue3-youtube'

const archetypeCounts = ref([
  {
    id: 0,
    archetype: 'Governante',
    text: 'Ordem, controle, segurança, responsabilidade, prestígio social.',
    count: 0,
    video: 'https://youtu.be/uU4-4EsR6gU'
  },
  {
    id: 1,
    archetype: 'Criador',
    text: 'Inovação, imaginação, criatividade, arte, liberdade.',
    count: 0,
    video: 'https://youtu.be/uU4-4EsR6gU'  
  },
  {
    id: 2,
    archetype: 'Cuidador',
    text: 'Cuidado, conexão, empatia, comprometimento.',
    count: 0,
    video: 'https://youtu.be/uU4-4EsR6gU'
  },
  {
    id: 3,
    archetype: 'Herói',
    text: 'Força, competência, coragem, competição, poder, revolução, segurança, certeza. ',
    count: 0,
    video: 'https://youtu.be/uU4-4EsR6gU'
  },
  {
    id: 4,
    archetype: 'Rebelde',
    text: 'Poder, rebeldia, revolução, quebra de paradigmas.',
    count: 0,
    video: 'https://youtu.be/uU4-4EsR6gU'
  },
  {
    id: 5,
    archetype: 'Sábio',
    text: 'Erudito, pesquisador, professor, especialista.',
    count: 0,
    video: 'https://youtu.be/uU4-4EsR6gU'
  },
  {
    id: 6,
    archetype: 'Explorador',
    text: 'Descoberta, individualismo, liberdade, autenticidade.',
    count: 0,
    video: 'https://youtu.be/uU4-4EsR6gU'
  },
  {
    id: 7,
    archetype: 'Inocente',
    text: 'Leveza, simplicidade, idealização, nostalgia, paz.',
    count: 0,
    video: 'https://youtu.be/uU4-4EsR6gU'
  },
  {
    id: 8,
    archetype: 'Cara Comum',
    text: 'Inclusão, pertencimento, igualdade, simplicidade.',
    count: 0,
    video: 'https://youtu.be/uU4-4EsR6gU'
  },
  {
    id: 9,
    archetype: 'Bobo da corte',
    text: 'Diversão, viver o momento presente, vida leve descontraída.',
    count: 0,
    video: 'https://youtu.be/uU4-4EsR6gU'
  },
  {
    id: 10,
    archetype: 'Mago',
    text: 'Poder, magia, tecnologia, consciência, universo, sincronicidade, soluções milagrosas, lei da atração, abundância.',
    count: 0,
    video: 'https://youtu.be/uU4-4EsR6gU'
  },
  {
    id: 11,
    archetype: 'Amante',
    text: 'Autoaceitação, felicidade, amor, êxtase, intimidade',
    count: 0,
    video: 'https://youtu.be/uU4-4EsR6gU'
  }])

const archetypeQuestions = ref([
{
  question: 'Sobre a sua personalidade, qual desses traços está mais presente em você?',
  options: [{
    id: 0,
    archetype: 'Governante',
    option: 'Ambicioso'
  },
  {
    id: 1,
    archetype: 'Criador',
    option: 'Criativo'
  },
  {
    id: 2,
    archetype: 'Cuidador',
    option: 'Amoroso/Cuidadoso'
  },
  {
    id: 3,
    archetype: 'Herói:',
    option: 'Forte/Resiliente'
  },
  {
    id: 4,
    archetype: 'Rebelde',
    option: 'Questionador/Revolucionário'
  },
  {
    id: 5,
    archetype: 'Sábio',
    option: 'Reflexivo/Estudioso/Sábio'
  },
  {
    id: 6,
    archetype: 'Explorador',
    option: 'Aventureiro/Viajante'
  },
  {
    id: 7,
    archetype: 'Inocente',
    option: 'Sonhador/Idealizador'
  },
  {
    id: 8,
    archetype: 'Cara Comum',
    option: 'Empático/Amigável'
  },
  {
    id: 9,
    archetype: 'Bobo da corte',
    option: 'Engraçado/Divertido'
  },
  {
    id: 10,
    archetype: 'Mago',
    option: 'Espiritual/Inspirador'
  },
  {
    id: 11,
    archetype: 'Amante',
    option: 'Romântico'
  }],
  selected: null
},
{
  question: 'Seus principais valores:',
  options: [
  {
    id: 0,
    archetype: 'Governante',
    option: 'Liderança, autoridade, ordem, controle, luxo, sucesso e poder'
  },
  {
    id: 1,
    archetype: 'Criador',
    option: 'Criatividade, curiosidade, integridade, inovação e imaginação'
  },
  {
    id: 2,
    archetype: 'Cuidador',
    option: 'Cuidado, compaixão, acolhimento e altruísmo'
  },
  {
    id: 3,
    archetype: 'Herói:',
    option: 'Coragem, ação, motivação, superação e disciplina'
  },
  {
    id: 4,
    archetype: 'Rebelde',
    option: 'Disrupção, quebra de padrões, questionamento, originalidade e revolução'
  },
  {
    id: 5,
    archetype: 'Sábio',
    option: 'Conhecimento, aprendizagem, lógica, razão e verdade'
  },
  {
    id: 6,
    archetype: 'Explorador',
    option: 'Liberdade, independência, dinamismo, aventura e natureza'
  },
  {
    id: 7,
    archetype: 'Inocente',
    option: 'Otimismo, esperança, simplicidade, bondade, pureza e felicidade'
  },
  {
    id: 8,
    archetype: 'Cara Comum',
    option: 'Inclusão, igualdade, pertencimento, comunidade e amizade'
  },
  {
    id: 9,
    archetype: 'Bobo da corte',
    option: 'Alegria, diversão, bom humor e leveza'
  },
  {
    id: 10,
    archetype: 'Mago',
    option: 'Inspiração, encantamento, magia, experiência, intuição, transformação e consciência'
  },
  {
    id: 11,
    archetype: 'Amante',
    option: 'Beleza, paixão, atração, relacionamento, desejo e sedução'
  }],
  selected: null
},
{
  question: 'Seu AMBIENTE preferido é um lugar:',
  options: [
  {
    id: 0,
    archetype: 'Governante',
    option: 'Chique, caro e luxuoso, que transmita poder e autoridade'
  },
  {
    id: 1,
    archetype: 'Criador',
    option: 'Que me dê inspiração para criar'
  },
  {
    id: 2,
    archetype: 'Cuidador',
    option: 'Confortável, aconchegante, acolhedor'
  },
  {
    id: 3,
    archetype: 'Herói:',
    option: 'Lugares diferentes, com pessoas e problemas/desafios para resolver'
  },
  {
    id: 4,
    archetype: 'Rebelde',
    option: 'Em que posso expressar meus ideiais e causas que acredito'
  },
  {
    id: 5,
    archetype: 'Sábio',
    option: 'Silencioso, e discreto, Onde posso escrever, estudar, refletir'
  },
  {
    id: 6,
    archetype: 'Explorador',
    option: 'É o mundo todo, onde eu me sinta livre para explorar e para me conectar com a natureza'
  },
  {
    id: 7,
    archetype: 'Inocente',
    option: 'Simples e delicado, onde me sinto em segurança para sonhar'
  },
  {
    id: 8,
    archetype: 'Cara Comum',
    option: 'Em que todos podem ser tratados com igualdade'
  },
  {
    id: 9,
    archetype: 'Bobo da corte',
    option: 'Festivo, leve, alegre, descontraído'
  },
  {
    id: 10,
    archetype: 'Mago',
    option: 'Enigmático, misterioso, místico'
  },
  {
    id: 11,
    archetype: 'Amante',
    option: 'Belo, sofisticado, romântico, com riqueza de detalhes'
  }],
  selected: null
},
{
  question: 'Seu estilo de liderança:',
  options: [
  {
    id: 0,
    archetype: 'Governante',
    option: 'Política/estratégica'
  },
  {
    id: 1,
    archetype: 'Criador',
    option: 'Visionária'
  },
  {
    id: 2,
    archetype: 'Cuidador',
    option: 'Paternalista ou servidora'
  },
  {
    id: 3,
    archetype: 'Herói:',
    option: 'Motivadora/coach'
  },
  {
    id: 4,
    archetype: 'Rebelde',
    option: 'Revolucionária'
  },
  {
    id: 5,
    archetype: 'Sábio',
    option: 'Especialista'
  },
  {
    id: 6,
    archetype: 'Explorador',
    option: 'Pioneira'
  },
  {
    id: 7,
    archetype: 'Inocente',
    option: 'Liberal'
  },
  {
    id: 8,
    archetype: 'Cara Comum',
    option: 'Democrática'
  },
  {
    id: 9,
    archetype: 'Bobo da corte',
    option: 'Leve e motivadora'
  },
  {
    id: 10,
    archetype: 'Mago',
    option: 'Carismático e/ou espiritual'
  },
  {
    id: 11,
    archetype: 'Amante',
    option: 'Facilitadora'
  }],
  selected: null
},
{
  question: 'Qual o seu maior dom?',
  options: [
  {
    id: 0,
    archetype: 'Governante',
    option: 'Liderança/poder/influência'
  },
  {
    id: 1,
    archetype: 'Criador',
    option: 'Criatividade'
  },
  {
    id: 2,
    archetype: 'Cuidador',
    option: 'Ajudar as pessoas no que necessitam/servir'
  },
  {
    id: 3,
    archetype: 'Herói:',
    option: 'Força, coragem, e motivar pessoas'
  },
  {
    id: 4,
    archetype: 'Rebelde',
    option: 'Quebrar paradigmas'
  },
  {
    id: 5,
    archetype: 'Sábio',
    option: 'Sabedoria/conhecimento acumulado'
  },
  {
    id: 6,
    archetype: 'Explorador',
    option: 'Ajudar as pessoas a serem livres, fugirem do tédio, viverem experiências novas e autênticas'
  },
  {
    id: 7,
    archetype: 'Inocente',
    option: 'Otimismo'
  },
  {
    id: 8,
    archetype: 'Cara Comum',
    option: 'Me conectar com as pessoas'
  },
  {
    id: 9,
    archetype: 'Bobo da corte',
    option: 'Ser engraçado/divertir as pessoas'
  },
  {
    id: 10,
    archetype: 'Mago',
    option: 'Ajudar pessoas em sua transformação pessoal ou espiritual'
  },
  {
    id: 11,
    archetype: 'Amante',
    option: 'Saber tornar as coisas ou pessoas atraentes física ou emocionalmente'
  }],
  selected: null
},
{
  question: 'Seus maiores defeitos:',
  options: [
  {
    id: 0,
    archetype: 'Governante',
    option: 'As vezes passo tanta autoridade, que passo uma imagem inacessível'
  },
  {
    id: 1,
    archetype: 'Criador',
    option: 'Perfeccionismo'
  },
  {
    id: 2,
    archetype: 'Cuidador',
    option: 'Penso muito nos outros e esqueço de mim mesma'
  },
  {
    id: 3,
    archetype: 'Herói:',
    option: 'Raramente exponho minhas fraquezas e sou muito competitivo'
  },
  {
    id: 4,
    archetype: 'Rebelde',
    option: 'As vezes sou crítico demais'
  },
  {
    id: 5,
    archetype: 'Sábio',
    option: 'Tenho muito conhecimento e pouca prática'
  },
  {
    id: 6,
    archetype: 'Explorador',
    option: 'Me entedio com facilidade, tenho vício em variedade'
  },
  {
    id: 7,
    archetype: 'Inocente',
    option: 'Fico na zona de conforto diversas vezes'
  },
  {
    id: 8,
    archetype: 'Cara Comum',
    option: 'Dependo das circunstâncias ou pessoas para estar bem e agir'
  },
  {
    id: 9,
    archetype: 'Bobo da corte',
    option: 'Fujo/evito demais os momentos de tristeza'
  },
  {
    id: 10,
    archetype: 'Mago',
    option: 'As vezes sou egoísta, ou convenço as pessoas de algo que só vai beneficiar a mim'
  },
  {
    id: 11,
    archetype: 'Amante',
    option: 'Necessidade de aprovação e/ou ciúme'
  }],
  selected: null
},
{
  question: 'Um lema que mais combina com você:',
  options: [
  {
    id: 0,
    archetype: 'Governante',
    option: '"Poder e influência são importantes"'
  },
  {
    id: 1,
    archetype: 'Criador',
    option: '"Se pode ser imaginado, pode ser criado"'
  },
  {
    id: 2,
    archetype: 'Cuidador',
    option: '"Ame ao próximo como a si mesmo"'
  },
  {
    id: 3,
    archetype: 'Herói:',
    option: '"Onde há uma vontade há um caminho"'
  },
  {
    id: 4,
    archetype: 'Rebelde',
    option: '"Regras foram feitas para serem quebradas"'
  },
  {
    id: 5,
    archetype: 'Sábio',
    option: '"A verdade liberta"'
  },
  {
    id: 6,
    archetype: 'Explorador',
    option: '"Não coloque cercas a minha volta"'
  },
  {
    id: 7,
    archetype: 'Inocente',
    option: '"O essencial é simples"'
  },
  {
    id: 8,
    archetype: 'Cara Comum',
    option: '"Todos são iguais"'
  },
  {
    id: 9,
    archetype: 'Bobo da corte',
    option: '"Só se vive uma vez"'
  },
  {
    id: 10,
    archetype: 'Mago',
    option: '"Meu pensamento faz as coisas acontecerem"'
  },
  {
    id: 11,
    archetype: 'Amante',
    option: '"Cada pessoa é única"'
  }],
  selected: null
},
{
  question: 'Palavras-chave que melhor te definem:',
  options: [
  {
    id: 0,
    archetype: 'Governante',
    option: 'Chefe, líder, ditador, general, presidente'
  },
  {
    id: 1,
    archetype: 'Criador',
    option: 'Artista, inovador, inventor, músico, escritor, poeta'
  },
  {
    id: 2,
    archetype: 'Cuidador',
    option: 'Altruísta, mãe/pai, cuidador, apoiador, ajudante'
  },
  {
    id: 3,
    archetype: 'Herói:',
    option: 'Guerreiro, salvador, super-herói, atleta, vencedor'
  },
  {
    id: 4,
    archetype: 'Rebelde',
    option: 'Fora da lei, revolucionário, disruptivo'
  },
  {
    id: 5,
    archetype: 'Sábio',
    option: 'Perito, especialista, conselheiro, pensador, filósofo, mentor, professor'
  },
  {
    id: 6,
    archetype: 'Explorador',
    option: 'Aventureiro, peregrino, individualista'
  },
  {
    id: 7,
    archetype: 'Inocente',
    option: 'Utópico, tradicionalista, ingênuo, sonhador, romântico, Poliana'
  },
  {
    id: 8,
    archetype: 'Cara Comum',
    option: 'Bom vizinho, bom cidadão, pessoa da porta ao lado, amigo'
  },
  {
    id: 9,
    archetype: 'Bobo da corte',
    option: 'Brincalhão, animador, performático'
  },
  {
    id: 10,
    archetype: 'Mago',
    option: 'Visionário, inovador, líder carismático, curandeiro, místico, feiticeiro, mágico'
  },
  {
    id: 11,
    archetype: 'Amante',
    option: 'Parceiro, Cônjuge, Íntimo, Casamenteiro, Sensualista'
  }],
  selected: null
},
{
  question: 'Seu propósito ou propósito da sua empresa:',
  options: [
  {
    id: 0,
    archetype: 'Governante',
    option: 'Criar uma família, empresa ou comunidade bem sucedida e próspera, e me tornar uma referência para as pessoas'
  },
  {
    id: 1,
    archetype: 'Criador',
    option: 'Criar coisas de valor duradouro, uma obra, uma mensagem, um ambiente que seja significativo e que fique marcado na mente das pessoas'
  },
  {
    id: 2,
    archetype: 'Cuidador',
    option: 'Ajudar as pessoas a se sentirem seguras e nutridas, a cuidarem de si mesmas, a estarem conectadas umas as outras'
  },
  {
    id: 3,
    archetype: 'Herói:',
    option: 'Ajudar as pessoas a agirem com coragem e protagonismo, e alcançarem melhores resultados'
  },
  {
    id: 4,
    archetype: 'Rebelde',
    option: 'Ajudar as pessoas a deixarem para trás o que precisa morrer, para que possam renascer e revolucionar o mundo'
  },
  {
    id: 5,
    archetype: 'Sábio',
    option: 'Ajudar as pessoas a pensarem, compreenderem o mundo em que vivem e a tomar decisões mais inteligentes'
  },
  {
    id: 6,
    archetype: 'Explorador',
    option: 'Ajudar as pessoas a serem livres e independentes e a expressarem sua individualidade no mundo'
  },
  {
    id: 7,
    archetype: 'Inocente',
    option: 'Ajudar as pessoas a serem mais felizes através da minha bondade e otimismo'
  },
  {
    id: 8,
    archetype: 'Cara Comum',
    option: 'Ajudar as pessoas a se aceitarem como são e se sentirem parte de uma comunidade'
  },
  {
    id: 9,
    archetype: 'Bobo da corte',
    option: 'Ajudar as pessoas a se divertirem, a viverem a vida no presente, a serem mais alegres e espontâneas'
  },
  {
    id: 10,
    archetype: 'Mago',
    option: 'Ajudar as pessoas em suas jornadas de transformação pessoal e cura'
  },
  {
    id: 11,
    archetype: 'Amante',
    option: 'Fazer com que as pessoas se sintam amadas e especiais, ajudá-las a conquistar outras pessoas e a construir relações em que possam dar e receber amor'
  }],
  selected: null
},
{
  question: 'Sua maior crença:',
  options: [
  {
    id: 0,
    archetype: 'Governante',
    option: 'Somos responsáveis por nossa vida e por nossos resultados'
  },
  {
    id: 1,
    archetype: 'Criador',
    option: 'O mundo está cheio de mais do mesmo, precisamos inovar'
  },
  {
    id: 2,
    archetype: 'Cuidador',
    option: 'É dando que se recebe'
  },
  {
    id: 3,
    archetype: 'Herói',
    option: 'Acredito que o mundo não é para os fracos. precisamos de padrões elevados de conduta para vencer nossos desafios'
  },
  {
    id: 4,
    archetype: 'Rebelde',
    option: 'Acredito nas mudanças e que as vezes é preciso quebrar regras para que elas aconteçam'
  },
  {
    id: 5,
    archetype: 'Sábio',
    option: 'Podemos encontrar a verdade por meio do conhecimento'
  },
  {
    id: 6,
    archetype: 'Explorador',
    option: 'Preciso renunciar a segurança para garantir a autonomia e liberdade'
  },
  {
    id: 7,
    archetype: 'Inocente',
    option: 'O mundo é um lugar bom, sem maldade. quem é mau é mau porque algo lhe foi feito. Vejo sempre o melhor nas pessoas'
  },
  {
    id: 8,
    archetype: 'Cara Comum',
    option: 'Posso abrir mão de mim mesmo para fazer parte de algo maior'
  },
  {
    id: 9,
    archetype: 'Bobo da corte',
    option: 'Precisamos viver o momento presente'
  },
  {
    id: 10,
    archetype: 'Mago',
    option: 'É possível criar novas realidades a partir da mudança de consciência'
  },
  {
    id: 11,
    archetype: 'Amante',
    option: 'É possível e necessário viver o amor no relacionamento e no meu trabalho'
  }],
  selected: null
},
{
  question: 'Seu maior medo:',
  options: [
  {
    id: 0,
    archetype: 'Governante',
    option: 'Viver no caos e ser destituído'
  },
  {
    id: 1,
    archetype: 'Criador',
    option: 'Ter uma vida medíocre ou igual a de todos'
  },
  {
    id: 2,
    archetype: 'Cuidador',
    option: 'Ingratidão, egoísmo, ou acontecer algo de ruim com alguém que esteja sob meus cuidados'
  },
  {
    id: 3,
    archetype: 'Herói:',
    option: 'Perder o controle da situação, demonstrar fraqueza e me tornar covarde'
  },
  {
    id: 4,
    archetype: 'Rebelde',
    option: 'Ser comum, impotente, inconsequente ou ineficaz'
  },
  {
    id: 5,
    archetype: 'Sábio',
    option: 'Ser enganado, iludido ou me tornar ignorante'
  },
  {
    id: 6,
    archetype: 'Explorador',
    option: 'Ficar preso na armadilha da conformidade ou vazio interior'
  },
  {
    id: 7,
    archetype: 'Inocente',
    option: 'Me expor ao ridículo, ser punido, desagradar as pessoas.'
  },
  {
    id: 8,
    archetype: 'Cara Comum',
    option: 'Me destacar demais ou parecer que tenho mais importância que as outras pessoas, parecer esnobe ou exibido.'
  },
  {
    id: 9,
    archetype: 'Bobo da corte',
    option: 'Aborrecer-se ou ser maçante'
  },
  {
    id: 10,
    archetype: 'Mago',
    option: 'Ter consequências negativas inesperadas e não intencionais'
  },
  {
    id: 11,
    archetype: 'Amante',
    option: 'Ficar sozinho, ser indesejado '
  }],
  selected: null
},
{
  question: 'Seu maior desejo:',
  options: [
  {
    id: 0,
    archetype: 'Governante',
    option: 'Liderar, e obter os recursos necessários para restaurar a harmonia e a ordem'
  },
  {
    id: 1,
    archetype: 'Criador',
    option: 'Criar coisas de valor duradouro, uma obra, uma mensagem, um ambiente que seja significativo e que fique marcado na mente das pessoas'
  },
  {
    id: 2,
    archetype: 'Cuidador',
    option: 'Ajudar, proteger, e cuidar das pessoas. Ser lembrado por ter feito a minha parte.'
  },
  {
    id: 3,
    archetype: 'Herói:',
    option: 'Fazer o impossível, através de ações corajosas, superando todos os desafios. foco na resolução de problemas'
  },
  {
    id: 4,
    archetype: 'Rebelde',
    option: 'Revolucionar, quebrar padrões, destruir algo que não funciona mais'
  },
  {
    id: 5,
    archetype: 'Sábio',
    option: 'Encontrar a verdade a partir de um cenário de confusão e dúvida'
  },
  {
    id: 6,
    archetype: 'Explorador',
    option: 'Liberdade para explorar novas coisas e trilhar uma jornada de autodescoberta e autenticidade'
  },
  {
    id: 7,
    archetype: 'Inocente',
    option: 'Vivenciar o paraíso. Através da minha pureza, bondade e simplicidade, busco viver experiências que me tragam paz e felicidade, nostalgia'
  },
  {
    id: 8,
    archetype: 'Cara Comum',
    option: 'estar em conexão com as pessoas, fazer parte de um grupo, pertencer'
  },
  {
    id: 9,
    archetype: 'Bobo da corte',
    option: 'Aproveitar a vida no momento presente, com alegria.'
  },
  {
    id: 10,
    archetype: 'Mago',
    option: 'Conhecer as leis fundamentais do universo.'
  },
  {
    id: 11,
    archetype: 'Amante',
    option: 'Criar intimidade e ter uma experiência de amor e prazer.'
  }],
  selected: null
},
{
  question: 'Seus clientes ideais se buscam em seu serviço:',
  options: [
  {
    id: 0,
    archetype: 'Governante',
    option: 'Obter segurança, ordem ou organização através de seus serviço'
  },
  {
    id: 1,
    archetype: 'Criador',
    option: 'Obter inspiração para criar, ou facilitar seu processo criativo'
  },
  {
    id: 2,
    archetype: 'Cuidador',
    option: 'Um meio de facilitar o cuidado que seu cliente possui com as pessoas que ama (Ex: algo que facilite o cuidado com os filhos ou com idosos)'
  },
  {
    id: 2,
    archetype: 'Cuidador',
    option: 'Um meio de autocuidado (para clientes que já se doam demais pelos outros, como mães ou pessoas altamente altruístas)'
  },
  {
    id: 3,
    archetype: 'Herói:',
    option: 'Motivação, inspiração ou ferramentas para superar obstáculos em suas jornadas e vencer'
  },
  {
    id: 4,
    archetype: 'Rebelde',
    option: 'Algo diferente da maioria, que quebra paradigmas, que é revolucionário, diferente do que a maioria nesse nicho apresenta'
  },
  {
    id: 5,
    archetype: 'Sábio',
    option: 'Agir de modo mais inteligente e tomar boas decisões'
  },
  {
    id: 6,
    archetype: 'Explorador',
    option: 'Se descobrir em sua nova jornada de vida e/ou alcançar a liberdade'
  },
  {
    id: 6,
    archetype: 'Explorador',
    option: 'Trilhar uma jornada diferente da maioria, ser autêntico/único'
  },
  {
    id: 7,
    archetype: 'Inocente',
    option: 'Viver seus sonhos, viver experiências mágicas que sempre idealizou'
  },
  {
    id: 7,
    archetype: 'Inocente',
    option: 'Viver uma vida simples, leve e feliz'
  },
  {
    id: 8,
    archetype: 'Cara Comum',
    option: 'Fazer novas amizades. Se conectar com pessoas. Pertencer a um grupo.'
  },
  {
    id: 9,
    archetype: 'Bobo da corte',
    option: 'Viver o momento presente, curtir, se divertir'
  },
  {
    id: 10,
    archetype: 'Mago',
    option: 'Se curar, ou encontrar soluções milagrosas para seus problemas'
  },
  {
    id: 11,
    archetype: 'Amante',
    option: 'Se sentirem atraentes e/ou amados. Ou viver um romance'
  }],
  selected: null
}
])

const quizCompleted = ref(false)
const quizIntro = ref(true)
const currentQuestion = ref(0)

let archetypePercentage = []
let threeHighestPercentages = []
let optionSelected = null

const startQuiz = evt => {
  quizIntro.value = false
}

const getCurrentQuestion = computed(() => {
  let question = archetypeQuestions.value[currentQuestion.value]
  question.index = currentQuestion.value
  return question
})

const isFirtQuestion = computed(() => {
  if(getCurrentQuestion.value.index === 0) {
    return true
  }
  return false
})

const SetAnswer = evt => {
  archetypeQuestions.value[currentQuestion.value].selected = evt.target.value
  evt.target.value = null
}

const previusQuestion = () => {
  removeCount()
  currentQuestion.value--
}

const searchIdOptions = (indexQuestion, indexOption) => {
  return archetypeQuestions.value[indexQuestion]?.options[indexOption]?.id
}

const NextQuestion = () => {
  optionSelected = archetypeQuestions.value[currentQuestion.value].selected
  SetCount(searchIdOptions(currentQuestion.value, archetypeQuestions.value[currentQuestion.value].selected))
  if (currentQuestion.value < archetypeQuestions.value.length - 1) {
    currentQuestion.value++
  } else {
    quizCompleted.value = true
    setThreeHighestPercentages()
  }
}

const SetCount = (selectedOption) => {
  archetypeCounts.value.forEach(element => {
    if (element.id == selectedOption) {
      element.count++
    }
  });
}

const removeCount = () => {
  archetypeCounts.value.forEach(element => {
    if (element.id == optionSelected) {
      element.count--
    }
  });
}

const getThreeLargestObjects = (arr, property) => {
  arr.sort((a, b) => b[property] - a[property]);
  return arr.slice(0, 3);
}

const calcPercentage = (value) => {
  const percentage = (value/13) * 100
  return percentage
}

const setThreeHighestPercentages = () => {
  let i = 0
  archetypeCounts.value.forEach(element => {
    archetypePercentage[i] = {achertype: element.archetype, text: element.text, percentage: calcPercentage(element.count), video: element.video}
    // console.log('Obj: ', archetypePercentage[i])
    i++
  })
  threeHighestPercentages = getThreeLargestObjects(archetypePercentage, 'percentage')
  console.log('3maiores: ', threeHighestPercentages)
}
</script>

<template>
  <main class="app">
    <section 
      v-if="quizIntro"
      class="intro-section">
      <h1 class="intro-title">Qual é o seu <span class="intro-title-archetype">arquétipo</span>?</h1>
      <p class="intro-text">
        Para que seu resultado seja assertivo, 
        leia com calma todas as alternativas, 
        e mesmo que fique em dúvida entre mais de uma,
        escolha a que prevalecer em sua personalidade ou aspecto do seu negócio.
      </p>
      <div class="intro-wrapper">
        <button 
          class="start-quiz-button"
          @click="startQuiz">
            Começar
          </button>
          <hr class="line">
      </div>
      <div class="img-wrapper">
        <img class="logo-img" src="./assets/images/prancheta_1_copia_14.png" alt="Logo">
      </div>
    </section>

    <section class="quiz" v-else-if="!quizCompleted && !quizIntro">
      <div class="quiz-info">
        <span class="question">{{ getCurrentQuestion.question }}</span>
      </div>
      <div class="options">
        <label 
          v-for="(option, index) in getCurrentQuestion.options" 
          :key="index"
          :class="`option ${
            getCurrentQuestion.selected == index
              ? 'selected'
              : ''
          }`">

          <input 
            type="radio" 
            :name="getCurrentQuestion.index"
            :value="index"
            v-model="getCurrentQuestion.selected"
            @change="SetAnswer">
            <span>{{ option.option }}</span>
        </label>
      </div>

      <div class="wrapper-button">
        <button
          v-if="!isFirtQuestion"
          class="return-button"
          @click="previusQuestion"
        >
        Voltar
        </button>
        <button
          class="next-button"
          @click="NextQuestion"
          :disabled="!getCurrentQuestion.selected">
          {{ 
            getCurrentQuestion.index == archetypeQuestions.length - 1
              ? 'Finalizar'
              : getCurrentQuestion.selected == null
                ? 'Selecione uma opção'
                : 'Avançar'
          }}
        </button>
      </div>
    </section>
    
    <section v-else>
      <h1 class="final-title"><span class="congrats">Parabéns!</span> Analisei os dados do seu perfil e aqui abaixo estão os arquétipos que mais combinam com você! </h1>
      <div class="result-component">
        <div class="result-wrapper">
          <div class="archetype-wrapper">
            <p class="first-archetype">{{ threeHighestPercentages[0].achertype }}: {{ parseInt(threeHighestPercentages[0].percentage) }}%</p>
            <p class="archetype-text">{{ threeHighestPercentages[0].text }}</p>
            <div class="video">
              <YouTube width="100%" :src="threeHighestPercentages[0].video" ref="youtube">
                Seu navegador não suporta o vídeo.
              </YouTube>
            </div>
          </div>
          <div class="archetype-wrapper" v-if="threeHighestPercentages[1].percentage">
            <p class="second-archetype">{{ threeHighestPercentages[1].achertype }}: {{ parseInt(threeHighestPercentages[1].percentage) }}%</p>
            <p class="archetype-text">{{ threeHighestPercentages[1].text }}</p>
          </div>
          <div class="archetype-wrapper-last" v-if="threeHighestPercentages[2].percentage">
            <p class="third-archetype">{{ threeHighestPercentages[2].achertype }}: {{ parseInt(threeHighestPercentages[2].percentage) }}%</p>
            <p class="archetype-text">{{ threeHighestPercentages[2].text }}</p>
          </div>
        </div>
        <div>
          <p class="access-first-info">Para ter acesso às aulas de todos os arquétipos, basta entrar em sua área de membros.</p>
          <a 
            class="access-button" 
            target="_blank"
            href="https://sso.hotmart.com/login?service=https://purchase.hotmart.com/?_gl=1*1chgn4f*_ga*MTQwNzEyNDQ1OC4xNjc2NjQwODk5*_ga_GQH2V1F11Q*MTY3NjczNDQ3Ni41LjEuMTY3NjczNTM3Ny41Ny4wLjA.&renew=true"
          >
            Acessar
          </a>
          <p class="access-second-info">Ao acessá-la, o próximo passo será assistir o módulo “Aulas de aplicação” para saber como usar seus principais arquétipos de forma prática em suas redes sociais e demais lugares.</p>
          <p class="msg">Boas aulas!</p>
        </div>
      </div>
    </section>
  </main>
</template>

<style>
@font-face {
  font-family: 'Brown Sugar';
  src: url('../src/assets/fonts/Brown_Sugar.otf') format('truetype');
}

@font-face {
  font-family: 'Claster Oleander';
  src: url('../src/assets/fonts/Claster_Oleander.otf') format('truetype');
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  background-image: url('./assets/images/img-noise-361x370.png');
  background-repeat: repeat;
}

.app {
  display: flex;
  flex-direction: column;
  padding: 2rem;
  min-height: 100vh;
}

h1 {
  font-weight: 2rem;
  margin-bottom: 2rem;
}

.intro-title {
  font-family: 'Claster Oleander';
  font-weight: 500;
  font-size: 6em;
  color: #227382;
  margin: 40px 0;
}

.intro-title-archetype {
  font-family: 'Brown Sugar';
  color: #C5A361;
}

.intro-text {
  font-family: 'Poppins', sans-serif;
  font-weight: 500;
  font-size: 1.5em;
  color: #585858;
}

.attention {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  
}

.intro-wrapper {
  display: flex;
  margin-top: 70px;
}

.start-quiz-button {
  appearance: none;
  outline: none;
  border: none;
  cursor: pointer;

  background-image: linear-gradient(to right, #C5A361, #DFC694);
  border-radius: 8px;
  font-size: 1.3em;
  font-weight: 500;
  font-family: 'Claster Oleander';
  padding: 15px 55px;
  color: #000;
}

.start-quiz-button:hover {
  opacity: 80%;
}

.line {
  border: 1% solid black;
  width: 100%;
  height: 0;
  margin: 20px 0 20px 50px;
}

.img-wrapper {
  display: flex;
  justify-content: left;
  margin-top: 50px;
}

.logo-img {
  width: 180px;
  height: auto;
  opacity: 70%;
}

.quiz {
  background-color: #C9BCB3;
  padding: 1rem;
  width: 100%;
  max-width: 640px;
  border-radius: 0.5rem;
  align-self: center;
  flex-wrap: wrap;
}

.quiz-info {
  display: flex;
  justify-content: space-between;
  margin-bottom: 1rem;
}

.quiz-info .question {
  color: black;
  font-size: 2rem;
  font-family: 'Claster Oleander';
}

.quiz-info .score {
  color: #FFF;
  font-size: 1.25rem;
}

.options {
  margin-bottom: 1rem;
}

.option {
  display: block;
  padding: 1rem;
  color: #E6D9D9;
  background-color: #227382;
  margin-bottom: 0.5rem;
  border-radius: 0.5rem;
  cursor: pointer;
  font-family: 'Poppins', sans-serif;
}

.option:hover {
  background-color: #DFC694;
  color: #000;
}

.option.correct {
 background-color: #2cce7d;
}

.option.wrong {
  background-color: #ff5a5f;
}

.option.selected {
  color: #000;
 background-color: #C5A361;
}

.option:last-of-type {
  margin-bottom: 0;
}

.option.disabled {
  opacity: 0.5;
}

.option input {
  display: none;
}

.wrapper-button {
  text-align: right;
}

.return-button, .next-button  {
  appearance: none;
  outline: none;
  border: none;
  cursor: pointer;

  padding: 0.5rem 1rem;
  background-image: linear-gradient(to right, #C5A361, #DFC694);
  color: #2d213f;
  border-radius: 8px;
  font-size: 1.3em;
  font-weight: 500;
  font-family: 'Claster Oleander';
}

.return-button {
  float: left;
}

.final-title {
  font-family: 'Claster Oleander';
  font-weight: 500;
  font-size: 3em;
  color: #227382;
  margin: 10px 0 50px 0;
  text-align: center;
}

.congrats {
  color: #C5A361; 
  font-family: 'Brown Sugar';
}

.result-component {
  background-color: #C9BCB3;
  border-radius: 0.5rem;
  padding: 1.5rem;
}

.result-wrapper {
  background-color: #227382;
  border-radius: 0.5rem;
  padding: 20px 10px;
  box-shadow: 0 0 20px #868584;
}

.archetype-wrapper {
  margin-bottom: 70px;
  text-align: center;
}
.archetype-wrapper-last {
  text-align: center;
  margin-bottom: 5px;
}

.first-archetype, .second-archetype, .third-archetype {
  font-family: 'Claster Oleander';
  
  font-weight: 600;
  color: #C5A361;
  margin-bottom: 10px;
}

.first-archetype, .second-archetype, .third-archetype {
  font-size: 3em;
}

.video {
  margin: 20px auto 0 auto;
  max-width: 640px;
  max-height: 360px;
}

.archetype-text {
  color: #DFC694;
  font-size: 1.5em;
  font-family: 'Poppins', sans-serif;
}

.access-button {
  appearance: none;
  outline: none;
  border: none;
  cursor: pointer;

  background-image: linear-gradient(to right, #C5A361, #DFC694);
  border-radius: 8px;
  font-size: 1.3em;
  font-weight: 500;
  font-family: 'Claster Oleander';
  padding: 15px 55px;
  color: #000;
  display: block;
  margin: 0 auto;
  text-align: center;
  width: 200px;
  text-decoration: none;
}

.access-button:hover {
  opacity: 80%;
}

.access-first-info, .access-second-info {
  text-align: center;
  margin: 20px 0;
}

.access-first-info {
  font-size: 2.5em;
  font-family: 'Claster Oleander';
  color: #227382;
  margin-top: 50px;
}

.access-second-info {
  font-family: 'Poppins', sans-serif;
  color: #585858;
  font-size: 1.5em;
}

.msg {
  color: #C5A361;
  text-align: center;
  font-family: 'Brown Sugar';
  font-weight: 700;
  font-size: 4em;
  margin: 20px 0; 
}

button:disabled {
  opacity: 0.5;
}

h2 {
  font-size: 2rem;
  margin-bottom: 2rem;
  text-align: center;
}

p {
  color: #8f8f8f;
  font-size: 1.25rem;
}

@media screen and (max-width: 970px) {
  .intro-title {
    font-size: 5em;
  }

}

@media screen and (max-width: 820px) {
  .intro-title {
    font-size: 4em;
  }
}

@media screen and (max-width: 434px) {
  .first-archetype, .second-archetype, .third-archetype {
    font-size: 2em;
  }
  .archetype-text {
    font-size: 1em;
  }
}

@media screen and (max-width: 669px) {
  .intro-title {
    font-size: 3em;
  }
}

@media screen and (max-width: 560px) {
  .intro-title {
    text-align: center;
    margin-top: 20px;
  }
  .intro-text {
    font-size: 1.2em;
    text-align: center;
  }
  .intro-wrapper {
    margin-top: 40px;
  }
  .img-wrapper {
    justify-content: center;
  }
  .logo-img {
    width: 120px;
  }
  .start-quiz-button {
    display: block;
    margin: 0 auto;
    text-align: center;
  }
  .line {
    display: none;
  }
}

@media screen and (max-width: 373px) {
  .return-button, .next-button {
    font-size: 0.9em;
  }
}
</style>
