# combinedcolumn
Сombined DataColumn

Combining several columnы into one with using filters and sorting

composer require rikcage/yii2-combinedcolumn "*"

for use add in GridView columns

<?php Pjax::begin(); ?>    <?= GridView::widget([
        'dataProvider' => $dataProvider,
        'filterModel' => $searchModel,
        'columns' => [
            ['class' => 'yii\grid\SerialColumn'],

            item_id,
            item_name,
            [
				'class' => 'rikcage\combinedcolumn\CombinedDataColumn',
				'labelTemplate' => '{1}<br>{0}',
				'valueTemplate' => '{1} {0}',
				'filterTemplate' => '<div class="row"><div class="col-md-5">{1}</div><div class="col-md-6">{0}</div></div>',
				'labels' => [
					'currency',
					'amaunt',
				],
				'attributes'=>['currency:text','rate:text'],
				'values'=>['currency','rate'],
				'filters'=> [
					array('1' => 'usd', '3' => 'eur'), //select for currency
					null, //input for rate
				],
            ],
        ],
    ]); ?>
<?php Pjax::end(); ?>
